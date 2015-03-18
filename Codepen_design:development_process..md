#Proposal for Internal Codepen design/development process.

##Tools

**1.CodePen** - shelter account accessible by all

**2.Custom SCSS** - Hosted by us or on CodePen servers.

##Aim
Provide a rapid prototyping environment based on the Shelter pattern library that can be shared and iterated upon by all members of team, and used for presentations to other departments.

##Implementation

Once the master CSS/SCSS has been written and implemented into a style guide, this file will be loaded into CodePen or hosted by us and linked to by individual Pens.

The CSS for each HTML module will exist as mixins which, when applied to HTML elements, will propagate styles through the element and it's children. 

Designers will be able to rapidly iterate on modules that have been predefined and agreed upon by the team.

**eg.**

	<form class="donate-form">
		<input type="text" placeholder="Name">
		<input type="email" placeholder="Email">
		<input type="submit" value="Click me">
	</form>
	
In the above example a mixin applied to **.donate-form** might define the colour/padding/margin/font-family etc of the form itself and all of it's children.

A member of the team could create a standardised form, with a red submit CTA for instance, by simply applying the following SCSS to the form.

	.donate-form{
		@include donate_form-large(red);
	}

A benefit of this system over something like Axure is that the HTML and CSS can be entirely re-usable. Ideally a dev can simply pick up the code and run with it once it has been passed to them from the design team. And can be handed back, iterated on continuously or worked on in tandem with another team member.

####Upgradeable

This system also has the benefit of being fully upgradable in line with our style guide. As soon as the SCSS in the style guide is changed and committed to version control, it can be applied to all Pens and instantly find it's way into the prototyping process.

####Susy built in

CodePen has built in support for Susy which is potentially going to be our chosen grid system, or if we go with something like Bootstrap/Foundation, it can be linked to in the same way as our base stylesheet.

####HTML templating

CodePen comes with **HAML** <http://haml.info/> or **Jade** <http://jade-lang.com/> which look pretty good in terms of abstracting our HTML. They offer mixin style HTML creation. 

**eg. In Jade...**

	// Declaration
	mixin list
  	ul
    	li foo
    	li bar
    	li baz
    	
	// Use
	+list
	+list

**..would become**

	<ul>
  		<li>foo</li>
  		<li>bar</li>
  		<li>baz</li>
	</ul>
	<ul>
  		<li>foo</li>
  		<li>bar</li>
  		<li>baz</li>
	</ul>
	
We could set up mixins for our often used patterns that would take variables to generate the pattern's content and then be styled using SCSS mixins as demonstrated above. 

##In Conclusion, 

CodePen offers a form of rapid prototyping which we can use in line with our agreed and consistent styles as defined by the upcoming style guide. If we choose to use something like PatternLab, for our build process and creation of our pattern library, it is unclear whether this will be 100% compatible but at this stage this is all up for debate. 

#####Give me a nudge if you have any questions