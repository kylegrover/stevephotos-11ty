---
layout: layouts/page.njk
title: Yeah yeah whadya want?
---
I have prints and original paintings for sale. If you see something you like just let me know.<br><br>I also do custom artwork, including paintings and murals, and professional photography for events and businesses. 

<form method="post"
action="https://formbucket.com/f/buk_XyGYu1sO6VnHtYP5WhQY7kjG">
<input type="name" name="name" required>
<input type="email" name="email" required>
<input type="phone" name="phone">
<textarea name="message" required>
<button class="contact-submit g-recaptcha" data-sitekey="6Ld6h9sUAAAAADZtr4-r82pOF9swMvqrR_DsADsr" data-callback="contactPageSubmit">Send</button>
<div class="form-response"></div>
</form>

<script>
function contactPageSubmit(token) {
    var $form = $(".contact-page-form");
    var $btn = $('input[type=submit]', $form);
    var $form_response = $('.contact-page-form .form-response');

    if ($("input[name='_replyto']").val() === '') {
        $form_response.removeClass('success');
        $form_response.addClass('error');
        $form_response.html('Please enter an email address.');
        return
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
                $btn.prop('disabled', 'disabled');
            }
        })
        .done(function (response) {
            $form_response.addClass('success');
            $form_response.removeClass('error');
            $form_response.html('Thanks for contacting us, a representative will reach out to you as soon as possible');
            $btn.prop('disabled', false);
            $form.children('input, textarea').val('');
            $btn.val('Submit');
            console.log(response);
        })
        .fail(function (response) {
            $form_response.removeClass('success');
            $form_response.addClass('error');
            $form_response.html('Something went wrong, check the fields for errors and try submitting again');
            $btn.prop('disabled', false);
        })
};
</script>