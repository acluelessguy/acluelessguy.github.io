
## Subscribe to the Newsletter!!

<form id="subscription-form">
    <input type="email" placeholder="email" id="email" name="email" required>
    <input type="button" value="Subscribe!!" onclick="subscribeEmail()">
</form>

<div id="message"></div>

<script>
function subscribeEmail() {
    var emailInput = document.getElementById('email');
    var email = emailInput.value;
    var data = {
        email: email
    };

    fetch('https://hruz50c69c.execute-api.eu-west-3.amazonaws.com/default/addEmail', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(data)
    })
    .then(response => {
        if (response.ok) {
            return response.json();
        } else {
            throw new Error('Failed to subscribe');
        }
    })
    .then(data => {
        document.getElementById('message').innerText = 'Email successfully added to the newsletter!!';
        emailInput.value = ''; // Clear the email input box
    })
    .catch((error) => {
        document.getElementById('message').innerText = 'Subscription failed';
    });
}
</script>
