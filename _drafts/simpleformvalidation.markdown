---
layout: post
title:  "Simple Form Validation Plugin with Bootstrap/jQuery"
date:   2015-03-17
categories: interactive
---

<script>
(function($){
$.fn.limitChars= function(){
var $txt= this;

$txt.each(function(i, el){
var el = $(el);
el.after("<p class='help-block'></p>");
var $help = el.next().text(""),
$btn = $('.btn'),
$update = function(){

var charCount= el.val().length,
charMax= 20;

if (charCount > 0) {
$help.html(charCount + " characters entered. " + (charMax - charCount) + " remaining.");
$help.removeClass('bg-danger');
if (el.val().length < charMax){
$btn.removeClass('disabled');
}

if (charCount > charMax) {
$btn.addClass('disabled');
$help.addClass('bg-danger');
$help.text("Your message has exceeded the limit.");
}
}
else {
$help.text("");

}
};
el.keyup(function(){
$update();
}
);
}
);
return this;
}
}(jQuery));

$(document).ready(function(){
$('.form-control').limitChars();
});
</script>

<form>
<div class="row">
<div class="col-xs-6 col-centered">
<div class="form-group">
<label for="message1">Message #1</label>
<input type="text" class="form-control" id="message1">
<div class="form-group">
<button type="submit" class= "btn btn-default">Send</button>
</div>
</div>
</div>
</form>
