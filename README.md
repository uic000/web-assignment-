<?php

$events = [
    ["name" => "Music Concert", "date" => "2023-12-01"],
    ["name" => "Art Exhibition", "date" => "2023-12-15"],
    ["name" => "Tech Conference", "date" => "2024-01-10"]
];

$message = "";
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    
    $name = htmlspecialchars($_POST['name']);
    $email = htmlspecialchars($_POST['email']);
    $msg = htmlspecialchars($_POST['message']);
    
    
    $message = "Thank you, $name! Your message has been received.";
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dhaka Event Management</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background: #35424a;
            color: #ffffff;
            padding: 10px 0;
            text-align: center;
        }
        nav ul {
            list-style: none;
            padding: 0;
        }
        nav ul li {
            display: inline;
            margin: 0 15px;
        }
        nav ul li a {
            color: #ffffff;
            text-decoration: none;
        }
        main {
            padding: 20px;
        }
        footer {
            text-align: center;
            padding: 10px 0;
            background: #35424a;
            color: #ffffff;
            position: relative;
            bottom: 0;
            width: 100%;
        }
        .button {
            display: inline-block;
            padding: 10px 15px;
            background: #35424a;
            color: #ffffff;
            text-decoration: none;
            border-radius: 5px;
        }
        form {
            margin-top: 20px;
        }
        form label {
            display: block;
            margin: 10px 0 5px;
        }
        form input, form textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
        }
        form button {
            padding: 10px 15px;
            background: #35424a;
            color: #ffffff;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Dhaka Event Management</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#events">Events</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section id="home">
            <h2>Upcoming Events</h2>
            <p>Check out our latest events and join us!</p>
            <a href="#events" class="button">View Events</a>
        </section>
        
        <section id="events">
            <h2>Our Events</h2>
            <ul>
                <?php foreach ($events as $event): ?>
                    <li><?php echo $event['name']; ?> - Date: <?php echo $event['date']; ?></li>
                <?php endforeach; ?>
            </ul>
        </section>
        
        <section id="contact">
            <h2>Contact Us</h2>
            <?php if ($message): ?>
                <p><?php echo $message; ?></p>
            <?php endif; ?>
            <form method="POST" action="">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
                <label for="message">Message:</label>
                <textarea id="message" name="message" required></textarea>
                <button type="submit">Send Message</button>
            </form>
        </section>
    </main>
    <footer>
    <p>&copy; 2023 Dhaka Event Management</p>
    </footer>
</body>
</html>
