CSS-Coding-Standards
====================

Personal coding standards for crafting CSS

This document is a work in progress.

## Format

These are preferred formats for unminified CSS

* Prefer tabs to spaces when indenting CSS. (Developers can change Tab Size in their editors to choose desired width)
* Add a space after your selector(s).
* Order your CSS rules alphabetically.
* Put prefixed rules before the unprefixed rules.
* Line up prefixed styles.
* Add one line bewteen styles.
* Keep closing bracket on separate line.

  	.success {
			background-color: #dff0d8;
		  border-color: #d6e9c6;
		  color: #468847;
			-webkit-border-radius: 15px;
			   -moz-border-radius: 15px;
			        border-radius: 15px;
			font-weight: 700;
			width: 90%;
		}

		.error {
			background-color: #f2dede;
		  border-color: #eed3d7;
		  color: #b94a48;
			-webkit-border-radius: 15px;
			   -moz-border-radius: 15px;
			        border-radius: 15px;
		}

If you are minifing your CSS, include a link in a comment to view the unminified CSS.

## Stucture

Currently, the most efficient way to serve CSS to multiple devices is via 1 stylesheet. Try to keep all styles in one stylesheet to avoid additional HTTP requests. 

### Ordering your styles

Follow the SMACSS ordering strucure:

* Base
* Layout
* Modules
* States

### Base Styles

These consist of all HTML elements. Create styles just for the HTML elements you have on your site. If your building a CMS theme, where content will be generated by users, create styles for all HTML elements in case users add them through the CMS.

If you find that you have to overwrite your base styles often, refactor your base styles so the are more of a default.

### Layout Styles

In SMACSS, Johnathan talks about using the prefix `l-` to designate layout styles. I have not found a need for this to it is important to be aware of this practice. I know other developers are doing this as well. I typical find I don't need it.

Layout styles should be wrappers for modules, these are things like your website's header, footer, body, sidebar. Use classes for your layout styles. I've seen some people use attribute selectors like [role=header], though this makes your styles less reusable.

### Modules

Modules will make up a majority of your websites styles. There are three parts to modules.

* Modules
* Modifiers
* Subcomponents

**Naming Conventions**

There are [various naming conventions](LINK THIS). Below is my preferred naming convention for modules, modifiers, and subcomponents.

	.module {...}
	.module--modifier {...} /* Use double dash for modifiers */
	.module-subcomponent {...} /* Use single dash for subcomponents */
  .module-subcomponent--modifier {...} /* A modifier on a subcomponent */

If your module name is two or more words, use camel case. This allow dashes to represent distinctions between modules, modifiers, and subcomponents. 

    .moduleName {...} /* Correct */
    .productReviews {...}  /* Correct */
    .product-reviews {...} /* Incorrect */

Full example of the three parts of modules.

    .post {...}
    .post-title {...}
    .post-meta {...}
    .post-entry {...}
    .post-meta--sub{...}

## States

States styles are things like media queries, :hover, :focus, etc., and JavaScript states.

Include state styles that affect layout or module styles after the styles they are affecting.

As for generic states like, `is-hidden`, include these in a **State section** following your **Modules section** in your stylesheet.
