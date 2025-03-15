<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Squid Game : Le Livre - Téléchargement Gratuit</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 50px; }
        .container { max-width: 600px; margin: auto; padding: 20px; background: #f4f4f4; border-radius: 10px; }
        input, button { padding: 10px; margin: 10px 0; width: 100%; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Squid Game : Le Livre</h1>
        <p>Téléchargez gratuitement votre exemplaire !</p>
        <a href="Chapitre_1.pdf" download><button>Télécharger Maintenant</button></a>
        <p>Ou recevez-le par email :</p>
        <form action="send_email.php" method="POST">
            <input type="email" name="email" placeholder="Votre email" required>
            <button type="submit">Recevoir par Email</button>
        </form>
    </div>
</body>
</html>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST["email"])) {
    $email = filter_var($_POST["email"], FILTER_SANITIZE_EMAIL);
    
    if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $subject = "Téléchargement Gratuit : Squid Game - Le Livre";
        $message = "Merci d'avoir demandé le livre ! Vous pouvez le télécharger ici : https://votre-site.com/Chapitre_1.pdf";
        $headers = "From: contact@votre-site.com\r\nReply-To: contact@votre-site.com\r\nContent-Type: text/plain; charset=UTF-8";
        
        if (mail($email, $subject, $message, $headers)) {
            echo "Le lien de téléchargement a été envoyé à votre email.";
        } else {
            echo "Erreur lors de l'envoi de l'email.";
        }
    } else {
        echo "Adresse email invalide.";
    }
} else {
    echo "Requête invalide.";
}
?>

