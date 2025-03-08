Single Responsibility Principle (SRP)
public class Report
{
    public string Content { get; set; }
}

public class ReportPrinter
{
    public void Print(Report report)
    {
        Console.WriteLine($"Printing Report: {report.Content}");
    }
}

Open/Closed Principle (OCP)
public abstract class Shape
{
    public abstract double Area();
}

public class Circle : Shape
{
    public double Radius { get; set; }
    public override double Area() => Math.PI * Radius * Radius;
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }
    public override double Area() => Width * Height;
}

Liskov Substitution Principle (LSP)
public class Bird
{
    public virtual void Fly() => Console.WriteLine("Flying");
}

public class Sparrow : Bird { }

public class Penguin : Bird
{
    public override void Fly() => throw new NotImplementedException("Penguins cannot fly");
}

Interface Segregation Principle (ISP)
public interface IPrinter
{
    void Print();
}

public interface IScanner
{
    void Scan();
}

public class BasicPrinter : IPrinter
{
    public void Print() => Console.WriteLine("Printing...");
}

public class MultifunctionPrinter : IPrinter, IScanner
{
    public void Print() => Console.WriteLine("Printing...");
    public void Scan() => Console.WriteLine("Scanning...");
}

Dependency Inversion Principle (DIP)
public interface IMessageSender
{
    void SendMessage(string message);
}

public class EmailSender : IMessageSender
{
    public void SendMessage(string message) => Console.WriteLine($"Email sent: {message}");
}

public class NotificationService
{
    private readonly IMessageSender _messageSender;

    public NotificationService(IMessageSender messageSender)
    {
        _messageSender = messageSender;
    }

    public void Notify(string message)
    {
        _messageSender.SendMessage(message);
    }
}
