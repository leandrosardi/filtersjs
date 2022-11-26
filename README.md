![GitHub issues](https://img.shields.io/github/issues/leandrosardi/filtersjs) ![GitHub](https://img.shields.io/github/license/leandrosardi/filtersjs) ![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/leandrosardi/filtersjs) ![GitHub last commit](https://img.shields.io/github/last-commit/leandrosardi/filtersjs)


# Filters.Js
The **Filters.Js** is a little HTML widget to show nice filters that enhance the user experience.

[You can find a live example here](https://connectionsphere.com/developers/filtersjs).

**>>>> IF YOU LIKE THIS PROJECT, STAR IT ! <<<<** 

![image](https://i.ibb.co/3fQd581/pic1.png)

**Outline:**

1. [Getting Started](#1-getting-started)
2. [Lists of Allowed Values](#2-lists-of-allowed-values)
3. [Getting Keywords Added by the User](#3-getting-keywords-added-by-the-user)
4. [Adding Keywords](#4-adding-keywords)
5. [Removing Keywords](#5-removing-keywords)
6. [Events Handling](#6-events-handling)
7. [Using Filters.js as a MySaaS Extension](#7-using-filtersjs-as-a-mysaas-extension)
8. [Additional Notes](#8-additional-notes)
9. [Disclaimer](#9-disclaimer)
10. [Maintener](#10-maintainer)

## 1. Getting Started
Get started in 3 simple steps.

1. Download the required libraries and stylesheets.
All these files are included in this project. You can download them from this page.

2. Include them in the <header> section of your HTML page.

```html
<script src="jquery-3.5.1.min.js" type="text/javascript"></script>
<script src="commons.js" type="text/javascript"></script>
<link rel="stylesheet" href="./templates.css">
<script src="./filters.min.js" type="text/javascript"></script>
```

3. Create a nice filter.

```html
<input id='job positions' style='width:750px;' />
<script>
	var ctx = document.getElementById('keywords');
	$(document).ready(function() {
		filtersJs.draw(ctx, {
			allowed_positive_keywords: true, // default value: true
			allowed_negative_keywords: true, // default value: false
		});
	});
</script>
```

![image](https://i.ibb.co/NZLHByG/pic2.png)

**Use Case:** The include button will not be visible if the parameter allowed_positive_keywords is false.

**Use Case:** The exclude button will not be visible if the parameter allowed_positive_keywords is false or is not defined.

**Use Case:** Both include or exclude buttons remain disabled if there is no content written in the text field.

**Use Case:** The content in the text field is deleted after it is added as a new keyword.

**Use Case:** While writing on a textfield, the content is added as a positive keyword if the include button is enabled, and the user press ENTER.

**Use Case:** After add a new keyword, the focus is set on the input box, in order to allow the user to add many keywords using the keyboard only (usability).

## 2. Lists of Allowed Values

You can setup a limited list of values allowed to add to the filter.

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	$(document).ready(function() {
		filtersJs.draw(ctx, {
			allowed_positive_keywords: true,
			allowed_negative_keywords: true,
			allowed_values: [
				'Argentina',
				'Pakistan',
				'United States'
			]
		});
	});
</script>
```

![image](https://i.ibb.co/7JM6jdW/pic3.png)

**Use Case:** Both include or exclude buttons remain disabled if the content inside the input box does not match with any allowed value. The comparsion is not key-sensitive.

## 3. Getting Keywords Added by the User

You can get either positive keywords added to the filter,

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	filtersJs.getPositiveValues(ctx)
	// ['Argentina', 'Pakistan', 'United States']
</script>
```

or the negative keywords added to the filter too.

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	filtersJs.getNegativeValues(ctx)
	// ['India']
</script>
```

## 4. Adding Keywords

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	filtersJs.addValue(ctx, 'United Kingldom', true)
</script>
```

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	filtersJs.addValue(ctx, 'India', false)
</script>
```

## 5. Removing Keywords

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	filtersJs.removeValue(ctx, 'India')
	// no matter if the keyword was positive or negative
</script>
```

## 6. Events Handling

You can catch the event when either a value is added,

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	$(document).ready(function() {
		filtersJs.draw(ctx, {
			allowed_positive_keywords: true,
			on_add_value: function(value) {
				console.print('New value ' + value + ' has been added');
			},
		});
	});
</script>
```

or when a value is removed too.

```html
<input id='countries' style='width:750px;' />
<script>
	var ctx = document.getElementById('countries');
	$(document).ready(function() {
		filtersJs.draw(ctx, {
			allowed_negative_keywords: true,
			on_remove_value: function(value) {
				console.print('Value ' + value + ' has been removed');
			},
		});
	});
</script>
```

## 7. Using Filters.Js as a [MySaaS](https://github.com/leandrosardi/mysaas) Extension

If you are running a [MySaaS](https://github.com/leandrosardi/mysaas) project, you can add **Filters.js** as an extension.

Such an extension includes a code example screen (`/filtersjs`) that you show to other developers, for reference. 

Install **Filters.js** as an extension of [MySaaS](https://github.com/leandrosardi/mysaas) is pretty simple.

**Step 1:** Clone the project in the `extensions` filder.

```bash
cd ~/code/mysaas/extensions
git clone https://github.com/leandrosardi/filtersjs
```

**Step 2:** Add the extension to your `config.rb` file.

```ruby
BlackStack::Extensions.append :filtersjs
```

## 8. Additional Notes

The **Filters.Js** library is just starting on Jun-2021, and more functions will be added as needed.

The **Filters.Js** library has been written following the [**W3C JavaScript Best Practices**](https://www.w3.org/community/webed/wiki/JavaScript_best_practices).

## 9. Disclaimer

Use at your own risk. The use of the software and scripts downloaded on this site is done at your own discretion and risk and with agreement that you will be solely responsible for any damage to any computer system or loss of data that results from such activities.

## 10. Maintainer

Leandro Daniel Sardi <leandro((dot))sardi((@))expandedventure.com>