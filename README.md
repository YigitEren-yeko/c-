# c-
c#

using System;


    // Main Class
    class Program
    {
        // Entry Point Method
        static void Main(string[] args)
        {
            GetAppInfo(); // Run GetAppInfo function to get info

            GreetUser(); // Ask for users name and greet

            while (true)
            {

                // Init correct number
                //int correctNumber = 7;

                // Create a new Random object(number)
                Random random = new Random();

                // Init correct number
                int correctNumber = random.Next(1, 11);

                // Init guess var
                int GuessNumber = 0;

                // Ask user for number
                Console.Write("Guess a number between 1 and 10: ");

                // While guess is not correct
                while (GuessNumber != correctNumber)
                {
                    // Get users input
                    string UserInput = Console.ReadLine();

                    // Make sure its a number
                    if (!int.TryParse(UserInput, out GuessNumber))
                    {
                        // Print error message
                        PrintColorMessage(ConsoleColor.Red, "Please enter an actual number: ");

                        // Contineu
                        continue;
                    }

                    // Cast to int and put in guess
                    GuessNumber = Int32.Parse(UserInput);

                    // Match guess to correct number
                    if (GuessNumber != correctNumber)
                    {
                        // Print error message
                        PrintColorMessage(ConsoleColor.Red, "Wrong number, please try again!");
                    }
                }

                // Print success message
                PrintColorMessage(ConsoleColor.Green, "You are CORRECT!");

                // Ask to play again
                Console.Write("Play Again? [Y or N]: ");

                // Get answer
                string answer = Console.ReadLine().ToUpper();

                if (answer == "Y") {
                    continue;
                }
                else if (answer == "N") {
                    Console.WriteLine("Okay, see you for another game :)");
                    return;
                }
                else
                {
                    return;
                }
            }           

        }

        // Get and display app info
        static void GetAppInfo() {
            // Set app vars
            string AppName = "Number Guesser";
            string AppVersion = "1.1.2";
            string AppAuthor = "Mr.X";

            // Change text color
            //Console.ForegroundColor = ConsoleColor.Green;

            // Write out app info
            Console.WriteLine("{0}: Version {1} by {2}", AppName, AppVersion, AppAuthor);

            // Reset text color
            Console.ResetColor();
        }

        // Ask users name and greet
        static void GreetUser() {
            // Ask users name
            Console.Write("What is your name: ");

            // Get user input
            string inputName = Console.ReadLine();

            Console.WriteLine("Hello {0}, let's play a game :)", inputName);
        }

        // Print color message
        static void PrintColorMessage(ConsoleColor color, string message) {
            // Change text color
            Console.ForegroundColor = color;

            // Tell user its not a number
            Console.WriteLine(message);

            // Reset text color
            Console.ResetColor();
        }
    }
