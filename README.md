# operator.cs
public string FirstName { get; set; }

    
    public string LastName { get; set; }

    
    public static bool operator ==(Employee e1, Employee e2)
    {
        
        if (ReferenceEquals(e1, e2))
            return true;

        
        if ((object)e1 == null || (object)e2 == null)
            return false;

       
        return e1.Id == e2.Id;
    }

    
    public static bool operator !=(Employee e1, Employee e2)
    {
        return !(e1 == e2);
    }

    
    public override bool Equals(object obj)
    {
        var other = obj as Employee;
        if (other == null) return false;
        return this.Id == other.Id;
    }

   
    public override int GetHashCode()
    {
        return this.Id.GetHashCode();
    }
}


class Program
{
    static void Main(string[] args)
    {
        
        Employee emp1 = new Employee
        {
            Id = 1,
            FirstName = "Alice",
            LastName = "Smith"
        };

        
        Employee emp2 = new Employee
        {
            Id = 1,
            FirstName = "Bob",
            LastName = "Johnson"
        };

        
        Console.WriteLine("emp1 == emp2: " + (emp1 == emp2));  // Output: True

        
        Console.WriteLine("emp1 != emp2: " + (emp1 != emp2));  // Output: False

       
        Console.ReadLine();
    }
}
