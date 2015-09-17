# Facade Pattern
## Цел
* Целата на този модел е да скрие сложността на системата и да осигури на клиента един интерфейс, с
помощта на който клиентът може да ползва цялата функционалност. Този модел включва един клас, който
съдържа в себе си набор от под-класове, които са необходими за изпълнение на заявката на клиента. По
този начин Фасадата крие подробностите по самото изпълнение и предоставя готова функционалност.

## Употреба
* Този шаблон за дизайн може да се използва, когато една система е много сложна или трудна за разбиране
и/или има голям брой взаимосвързани класове.

## Имплементация 
 ```c#
 namespace IVSR.Designpattern.Facade
{
    class SubsystemA
    {
        public string OperationA1()
        {
            return "Subsystem A, Method A1\n";
        }
        public string OperationA2()
        {
            return "Subsystem A, Method A2\n";
        }
    }

    class SubsystemB
    {
        public string OperationB1()
        {
            return "Subsystem B, Method B1\n";
        }

        public string OperationB2()
        {
            return "Subsystem B, Method B2\n";
        }
    }

    class SubsystemC
    {
        public string OperationC1()
        {
            return "Subsystem C, Method C1\n";
        }

        public string OperationC2()
        {
            return "Subsystem C, Method C2\n";
        }
    }

    public class Facade
    {
        private SubsystemA a = new SubsystemA();
        private SubsystemB b = new SubsystemB();
        private SubsystemC c = new SubsystemC();
        public void Operation1()
        {
            Console.WriteLine("Operation 1\n" +
            a.OperationA1() +
            a.OperationA2() +
            b.OperationB1());
        }
        public void Operation2()
        {
            Console.WriteLine("Operation 2\n" +
            b.OperationB2() +
            c.OperationC1() +
            c.OperationC2());
        }
    }
}
 ``` 
 ## UML диаграма
 ![](https://upload.wikimedia.org/wikipedia/commons/e/e9/Decorator_UML_class_diagram.svg)
