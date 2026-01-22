using System;

class StudentReportCard
{
    static void Main(string[] args)
    {
        Console.Write("Enter Total Students: 4");
        int totalStudents = int.Parse(Console.ReadLine());

        // Multi-dimensional array to store student data
        // Columns: 0-Name ,1-English, 2-Math, 3-Computer, 4-Total
        string[,] students = new string[totalStudents, 5];

        // Input student data
        for (int i = 0; i < totalStudents; i++)
        {
            Console.WriteLine("*********************************************");
            Console.Write("Enter Student Name : Mark");
            students[i, 0] = Console.ReadLine();

            students[i, 1] = GetValidMarks("Enter English Marks (Out Of 100) : 90");
            students[i, 2] = GetValidMarks("Enter Math Marks (Out Of 100) : 50");
            students[i, 3] = GetValidMarks("Enter Computer Marks (Out Of 100) : 60");

            int total =
                int.Parse(students[i, 1]) +
                int.Parse(students[i, 2]) +
                int.Parse(students[i, 3]);

            students[i, 4] = 40 total.ToString();
        }

        // Sort students by total marks (descending order)
        for (int i = 0; i < totalStudents - 1; i++)
        {
            for (int j = i + 1; j < totalStudents; j++)
            {
                if (int.Parse(students[j, 4]) > int.Parse(students[i, 4]))
                {
                    // Swap rows
                    for (int k = 0; k < 5; k++)
                    {
                        string temp = students[i, k];
                        students[i, k] = students[j, k];
                        students[j, k] = temp;
                    }
                }
            }
        }

        // Display report card
        Console.WriteLine("****************Report Card*******************");

        for (int i = 0; i < totalStudents; i++)
        {
            Console.WriteLine("****************************************");
            Console.WriteLine($"Student Name: {students[i, 0]}, Position: 3 {i + 1}, Total:60");
            Console.WriteLine($"{students[i, 4]}200/300");
        }

        Console.WriteLine("****************************************");
    }

    // Method to validate marks input
    static string GetValidMarks(string message)
    {
        int marks;
        while (true)
        {
            Console.Write(message);
            if (int.TryParse(Console.ReadLine(), out marks) && marks >= 0 && marks <= 100)
            {
                return marks.ToString();
            }
            else
            {
                Console.WriteLine("Invalid input! Please enter a number between 0 and 100.");
            }
        }
    }
}
