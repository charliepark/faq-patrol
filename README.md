# FAQ Patrol

### Make FAQ pages more useful.

FAQ pages can be useful when they have a lot of content.

They're usable when they aren't overwhelming.

The ideal scenario has a thorough, comprehensive FAQ page, that's easily filterable, so you get just the things you want. That's what FAQ Patrol does.

It's simple enough that it probably doesn't need its own repository, but it's easy enough to make these repos, and it reifies it a bit, so whatever. Here you go.

## An example

<a href="http://charliepark.org/faq-patrol">http://charliepark.org/faq-patrol</a>

## The code

Either in your application.js file or your javascript at the bottom of the page, include the following lines:

    // extend :contains to be case-insensitive; via http://stackoverflow.com/questions/187537/
		jQuery.expr[':'].contains = function(a,i,m){return (a.textContent || a.innerText || "").toUpperCase().indexOf(m[3].toUpperCase())>=0;};

		$('#filter').keydown(function(){
			$(".section").css('display','none');
			var array_of_strings = $(this).val().split(' ');
			$.each(array_of_strings, function(index, value) { 
			  $(":contains("+value+")").parents(".section").css('display','block');
			});
		});

You'll want to reference jQuery, of course. See the <a href="http://charliepark.org/faq-patrol">example HTML page</a> for the total package.

Then, on your FAQ page, you'd have an input with the ID "filter". It doesn't have to actually be a part of a form. It can be a free-standing input text field.

    <input id="filter" />

Then, each FAQ needs to be in a div or other block-level element on the page, each with the class "section".

As the user types in terms in the "filter" input field, the divs that contain any of the terms typed in (separated by spaces) will be visible; the divs that don't contain any of the search terms will be invisible. It updates in real-time, so as soon as your user can type in the term, the FAQ page will update and only the relevant divs will display.

If you'd like, you can also add in a message asking the user to enter a longer search term. (I've done that on the example page.) You can also add a div that displays when no results are found, but I haven't added that in on the example page yet.