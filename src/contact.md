---
layout: layouts/page.njk
title: Yeah yeah whadya want?
---
<div>I have prints and original paintings for sale. If you see something you like just let me know.<br><br>I also do custom artwork, including paintings and murals, and professional photography for events and businesses. </div>

<div class="flex-768">
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
    <div class="contact-picture" style="margin: 10px; border-radius: 10px; background-image:url('../images/steve-painted.jpg'); background-size: cover; background-position: center bottom; background-repeat: no-repeat;min-height: 400px; "></div>
</div>

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
            $form_response.html('Wow... really? Well, I\'ll get back to you about that.');
            $btn.prop('disabled',false);
            $form.find('input, textarea').val('');
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