# pwolf
QLSV
using System;
using System.Collections.Generic;
using System.Linq;

public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }

    public override string ToString()
    {
        return $"ID: {Id,-3} | Ten: {Name,-15} | Tuoi: {Age}";
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        List<Student> students = new List<Student>()
        {
            new Student { Id = 1, Name = "Nguyen Van An", Age = 16 },
            new Student { Id = 2, Name = "Tran Thi Binh", Age = 19 },
            new Student { Id = 3, Name = "Le Van Chau", Age = 15 },
            new Student { Id = 4, Name = "Pham Thi Anh", Age = 18 },
            new Student { Id = 5, Name = "Hoang Van Dung", Age = 20 },
            new Student { Id = 6, Name = "Do Thi Giang", Age = 17 },
            new Student { Id = 7, Name = "Vu Van Anh", Age = 20 }
        };

        Console.WriteLine("--- QUAN LY DANH SACH HOC SINH BANG LINQ ---");

        Console.WriteLine("\na. Danh sach toan bo hoc sinh:");
        PrintStudents(students);

        Console.WriteLine("\nb. Danh sach hoc sinh co tuoi tu 15 den 18:");
        var studentsAge15To18 = students.Where(s => s.Age >= 15 && s.Age <= 18);
        PrintStudents(studentsAge15To18);

        Console.WriteLine("\nc. Danh sach hoc sinh co ten bat dau bang chu \"A\":");
        var studentsStartWithA = students.Where(s => s.Name.Split(' ').Last().StartsWith("A"));
        PrintStudents(studentsStartWithA);

        int totalAge = students.Sum(s => s.Age);
        Console.WriteLine($"\nd. Tong so tuoi cua tat ca hoc sinh la: {totalAge}");

        Console.WriteLine("\ne. Hoc sinh co tuoi lon nhat:");
        int maxAge = students.Max(s => s.Age);
        var oldestStudents = students.Where(s => s.Age == maxAge);
        PrintStudents(oldestStudents);

        Console.WriteLine("\nf. Danh sach hoc sinh sap xep theo tuoi tang dan:");
        var sortedStudents = students.OrderBy(s => s.Age);
        PrintStudents(sortedStudents);
    }

    public static void PrintStudents(IEnumerable<Student> studentList)
    {
        if (!studentList.Any())
        {
            Console.WriteLine("Khong tim thay hoc sinh nao phu hop.");
            return;
        }

        foreach (var student in studentList)
        {
            Console.WriteLine(student);
        }
    }
}
