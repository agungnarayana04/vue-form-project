<script>
  import RegisterForm from './components/Form.vue'
  export default {
    name : 'App',
    components : {RegisterForm}
  }
</script>

<template>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="x-apple-disable-message-reformatting">
    <title>Hotel Booking Form</title>
    <link href="https://fonts.googleapis.com/css?family=Montserrat" rel="stylesheet">
    <link rel="stylesheet" href="src/assets/button.css">
    <link rel="stylesheet" href="src/assets/blog.css">
    <link rel="stylesheet" href="src/assets/footer.css">
    <link rel="stylesheet" href="src/assets/hero.css">
    <link rel="stylesheet" href="src/assets/logo.css">
    
  </head>

  <body width="100%" style="margin: 0;  padding: 0 !important; mso-line-height-rule: exactly;">
    <center style="width: 100%; background-image: linear-gradient(#74b6d8, #4178c4);">
        <div
            style="display: none; font-size: 1px;max-height: 0px; 
            max-width: 0px; opacity: 0; overflow: hidden; 
            mso-hide: all; font-family:'Montserrat';">
        </div>

        <div style="max-width: 900px; margin: 0 auto;" class="email-container">
            <!-- BEGIN BODY -->

            <table :align="'center'" role="presentation" 
                cellspacing="0" cellpadding="0" 
                border="0" width="100%"
                style="margin: auto;">

                <tr><!-- start: tr hero-->

                    <td valign="middle" class="hero primary"
                        style="background-image: url(https://www.jotform.com/uploads/ugurg/form_files/hotel-banner.63885da4032201.67905415.png); 
                        background-size: cover; 
                        height: 300px;
                        background-position: center top;">
                    </td>
                </tr><!-- end tr hero-->

                <tr> <!-- start: tr header text-->

                    <td class="primary email-section">

                        <div class="heading-section" style="text-align: center; padding: 0 30px;">

                            <h2>Hotel Booking</h2>
                            <h3>Experience something new every moment</h3>

                        </div>

                    <div style="max-width: 600px;margin: auto; color: #000000; font-size: 14px;text-align: center;">
                      <RegisterForm/>
        </div>
        </td>
        </tr>
        </table>
        </div>
            <!-- End Body -->
    </center>
</body>
</template>

<style scoped>

</style>
