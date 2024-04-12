//Задание1
using System;

public interface IInterface
{
    void Method();
}

public class DerivedClass : IInterface
{
    public void Method()
    {
        Console.WriteLine("Метод, реализованный в классе DerivedClass");
    }
}

class Program
{
    static void Main()
    {
        DerivedClass dClass = new DerivedClass();
        dClass.Method();
    }
}
//Задание2
using System;

public interface IInterface
{
    double GetPI();
    int GetInt();
    double Square(int x);
    double Sqrt(int x);
}

public class MyClass : IInterface
{
    public double GetPI()
    {
        return Math.PI;
    }

    public int GetInt()
    {
        return 7;
    }

    public double Square(int x)
    {
        return x * x;
    }

    public double Sqrt(int x)
    {
        return Math.Sqrt(x);
    }
}

class Program
{
    static void Main()
    {
        MyClass myClass = new MyClass();
        Console.WriteLine("PI: " + myClass.GetPI());
        Console.WriteLine("Integer: " + myClass.GetInt());
        Console.WriteLine("Square of 5: " + myClass.Square(5));
        Console.WriteLine("Square root of 16: " + myClass.Sqrt(16));
    }
}
//Задание3
using System;

public interface IInterface1
{
    void Method1();
}

public interface IInterface2 : IInterface1
{
    void Method2();
}

public interface IInterface3 : IInterface2
{
    void Method3();
}

public class DerivedClass : IInterface3
{
    public void Method1()
    {
        Console.WriteLine("Метод Method1");
    }

    public void Method2()
    {
        Console.WriteLine("Метод Method2");
    }

    public void Method3()
    {
        Console.WriteLine("Метод Method3");
    }
}

class Program
{
    static void Main()
    {
        DerivedClass dClass = new DerivedClass();
        dClass.Method1();
        dClass.Method2();
        dClass.Method3();
    }
}
//Задание4
using System;

public interface IThinkable
{
    void Think();
}

public interface ITalkable
{
    void Talk();
}

public class Person : IThinkable, ITalkable
{
    public void Think()
    {
        Console.WriteLine("Я думаю...");
    }

    public void Talk()
    {
        Console.WriteLine("Привет, как дела?");
    }
}

class Program
{
    static void Main()
    {
        Person person = new Person();
        person.Think();
        person.Talk();
    }
}
//Задание5
using System;
using System.Collections.Generic;

public interface ISwitchable
{
    void TurnOn();
    void TurnOff();
}

public class TVSet : ISwitchable
{
    public void TurnOn()
    {
        Console.WriteLine("TV is turned on.");
    }

    public void TurnOff()
    {
        Console.WriteLine("TV is turned off.");
    }
}

public class PersonalComputer : ISwitchable
{
    public void TurnOn()
    {
        Console.WriteLine("PC is turned on.");
    }

    public void TurnOff()
    {
        Console.WriteLine("PC is turned off.");
    }
}

class Program
{
    static void Main()
    {
        List<ISwitchable> devices = new List<ISwitchable>();

        TVSet tv = new TVSet();
        devices.Add(tv);

        PersonalComputer pc = new PersonalComputer();
        devices.Add(pc);

        foreach (var device in devices)
        {
            device.TurnOn();
            device.TurnOff();
        }
    }
}
//Задание6
using System;

public interface IArithmeticOperations
{
    double Add(double a, double b);
    double Subtract(double a, double b);
    double Multiply(double a, double b);
    double Divide(double a, double b);
}

public interface IMathOperations
{
    double Square(double x);
    double SquareRoot(double x);
}

public class A : IArithmeticOperations
{
    public double Add(double a, double b)
    {
        return a + b;
    }

    public double Subtract(double a, double b)
    {
        return a - b;
    }

    public double Multiply(double a, double b)
    {
        return a * b;
    }

    public double Divide(double a, double b)
    {
        if (b == 0)
        {
            throw new DivideByZeroException("Cannot divide by zero.");
        }
        return a / b;
    }
}

public class Aa : A
{
    public new double Subtract(double a, double b)
    {
        return b - a; // Поменяем местами операнды при вычитании
    }

    public new double Divide(double a, double b)
    {
        if (a == 0)
        {
            throw new DivideByZeroException("Cannot divide by zero.");
        }
        return b / a; // Поменяем местами операнды при делении
    }
}

public class Ab : A, IMathOperations
{
    public double Square(double x)
    {
        return x * x;
    }

    public double SquareRoot(double x)
    {
        return Math.Sqrt(x);
    }
}

class Program
{
    static void Main()
    {
        Aa aa = new Aa();
        Console.WriteLine("Subtract(5, 3): " + aa.Subtract(5, 3));
        Console.WriteLine("Divide(10, 2): " + aa.Divide(10, 2));

        Ab ab = new Ab();
        Console.WriteLine("Square(4): " + ab.Square(4));
        Console.WriteLine("SquareRoot(16): " + ab.SquareRoot(16));
    }
}
//Задание7
using System;

public interface IPlayable
{
    void Play();
    void Pause();
    void Stop();
}

public interface IRecodable
{
    void Record();
    void Pause();
    void Stop();
}

public class Player : IPlayable, IRecodable
{
    public void Play()
    {
        Console.WriteLine("Playing...");
    }

    public void Pause()
    {
        Console.WriteLine("Pausing...");
    }

    public void Stop()
    {
        Console.WriteLine("Stopping...");
    }

    public void Record()
    {
        Console.WriteLine("Recording...");
    }
}

class Program
{
    static void Main()
    {
        Player player = new Player();
        
        Console.WriteLine("=== Playing ===");
        player.Play();
        player.Pause();
        player.Stop();

        Console.WriteLine("\n=== Recording ===");
        player.Record();
        player.Pause();
        player.Stop();
    }
}

