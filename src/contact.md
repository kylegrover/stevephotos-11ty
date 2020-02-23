---
layout: layouts/page.njk
title: Yeah yeah whadya want?
---
I have prints and original paintings for sale. If you see something you like just let me know.<br><br>I also do custom artwork, including paintings and murals, and professional photography for events and businesses. 

<form class="contact" method="post"
action="https://formbucket.com/f/buk_XyGYu1sO6VnHtYP5WhQY7kjG">
<h4>Questions & Unsolicited Advice</h4>
<div class="input-group"><label for="name">Name:</label><br>
<input type="name" name="name" required></div>
<div class="input-group"><label for="_replyto">Email:</label><br>
<input type="email" name="_replyto" required></div>
<div class="input-group"><label for="phone">Phone (optional):</label><br>
<input type="phone" name="phone"></div>
<div class="input-group"><label for="message">Message:</label><br>
<textarea name="message" required></textarea></div>
<button class="contact-submit g-recaptcha" data-sitekey="6Ld6h9sUAAAAADZtr4-r82pOF9swMvqrR_DsADsr" data-callback="contactPageSubmit">Send</button>
<div class="form-response"></div>
</form>

<script>
function contactPageSubmit(token) {
    var $form = $("form.contact");
    var $btn = $('input[type="submit"]', $form);
    var $form_response = $('.form-response', $form);

    if ($("input[name='_replyto']").value === '') {
        $form_response.removeClass('success');
        $form_response.addClass('error');
        $form_response.html('Please enter an email address.');
        return false;
    }

    $.ajax({
            url: $form.prop('action'),
            type: 'POST',
            crossDomain: true,
            headers: {
                'accept': 'application/javascript',
            },
            data: $form.serialize(),
            beforeSend: function () {
                $btn.prop('disabled','disabled');
            }
        })
        .done(function (response) {
            $form_response.addClass('success');
            $form_response.removeClass('error');
            $form_response.html('Thanks for contacting us, a representative will reach out to you as soon as possible');
            $btn.prop('disabled',false);
            $form.children('input, textarea').val('');
            $btn.val('Submit');
            console.log(response);
        })
        .fail(function (response) {
            $form_response.removeClass('success');
            $form_response.addClass('error');
            $form_response.html('Something went wrong, check the fields for errors and try submitting again');
            $btn.prop('disabled',false);
        })
};
</script>