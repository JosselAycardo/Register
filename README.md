<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Style.css">
    <title>Sign up</title>
</head>
<body>
    <div class="container">
        <div class="box form-box">

         <?php
           
           include("php/config.php");
           if(isset($_POST['submit'])){
            $username = $_POST['Username'];
            $email = $_POST['email'];
            $age = $_POST['Age'];
            $password = $_POST['Password'];
           
            $verify_query = mysqli_query($con,"SELECT Email FROM users WHERE Email ='$email'");

            if(mysqli_num_rows($verify_query) !=0){
                echo "<div class='message'
                         <p> This email is used, Try another one</p>
                         </div> <br>";
                echo "<a href='javascript:self.history.back()'> <button class ='btn'>Go Back</button>";
            }else{
                mysqli_query($con,"INSERT INTO users(USERNAME,EMAIL,AGE,PASSWORD) VALUES('$username','$email','$age','$password')") or die("Error Occured");
                echo "<div class='message'
                         <p> Registration Successfully</p>
                         </div> <br>";
                echo "<a href='index.php'> <button class ='btn'>Login Now</button>";
            }
            
        }else{
         ?>



            <header>Sign up</header>
            <form action="" method="post">
                <div class="field input">
                    <label for="Username">Username</label>
                    <input type="text" name="Username" id="Username" autocomplete="off" required>
                </div>
                <div class="field input">
                    <label for="email">Email</label>
                    <input type="text" name="email" id="email" autocomplete="off" required>
                </div>
                <div class="field input">
                    <label for="Age">Age</label>
                    <input type="number" name="Age" id="Age" autocomplete="off" required>
                </div>
                <div class="field input">
                    <label for="Password">Password</label>
                    <input type="password" name="Password" id="Password" autocomplete="off" required>
                </div>
                <div class="field">
                    <input type="submit" class="btn" name="submit" value="Register" required>
                </div>
                <div class="links">
                    Already have a account? <a href="index.php">Sign In</a>
                </div>
            </form>
        </div>
        <?php } ?>
    </div>
</script>
</body>
</html>
