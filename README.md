# Blade template and Laravel conflicts

As we know, both of them larvel blade template and angularjs use double curly brackets {{ }} for showing the value of variable. But we can solve this conflict by editing tags one of them or both.

## Change larvel blade template tags

Add above lines in app/routes.php:

`Blade::setContentTags('<%', '%>'); 		// for variables and all things Blade
 Blade::setEscapedContentTags('<%%', '%%>'); 	// for escaped data`

With above lines we can use instead of `{{ $variable }}` -> `<% $variable %>`, comments become `<%-- comment --%>` and escaped data will be `<%% $escapedVariable %%>`.

## Change angularjs tags
`var sampleApp = angular.module('sampleApp', [], function($interpolateProvider) {`
        `$interpolateProvider.startSymbol('<%');`
        `$interpolateProvider.endSymbol('%>');`
	`});`

As we can see, we used $interpolateProvider, which allows us to change the tags of angularjs. In this case `{{ variable }}` become `<% variable %>`.
