# Proxy Pattern
## Мотивация
* Междинен клас, който ни дава възможност да комуникираме с основния. Има различни приложения спрямо това кой вид Proxy ползваме - Remote, Virtual, Protection.

## Цел
* Remote Proxy - служи за обработване на данни при прехвърляне(кодира, прави статистика, логва информация).
* Virtual Proxy - служи за достъпване на допълнителна информация при евентуална нужда от нея и кеширането и.
* Protection Proxy - служи за добавяне на валидации и както за достъпване на ресурс, ако клиента е оторизиран.

## Употреба
* Добавяне на достъп за сигурност към съществуващ обект. Proxy ще определи дали клиентът има достъп до даден обект.
* Опростяване на API на сложни обекти. Proxy може да осигури прост API, така че кодът на клиента не трябва да се справя със сложността на обекта.
* Осигуряване на интерфейс за дистанционни ресурси, като например уеб услуга или REST ресурси.

## Имплементация
```c#
namespace IVSR.DesignPattern.Proxy
{
    interface ICar
    {
        void DriveCar();
    }

    //Real Object 
    public class Car : ICar
    {
        public void DriveCar()
        {
            Console.WriteLine("Car has been driven!");
        }
    }

    //Proxy Object
    public class ProxyCar : ICar
    {
        private Driver driver;
        private ICar realCar;

        public ProxyCar(Driver driver)
        {
            this.driver = driver;
            realCar = new Car();
        }

        public void DriveCar()
        {
            if (driver.Age <= 16)
                Console.WriteLine("Sorry, the driver is too young to drive.");
            else
                realCar.DriveCar();
         }
     }

    public class Driver
    {
        public int Age { get; set; }

        public Driver(int age)
        {
            this.Age = age;
        }
    }

    //How to use above Proxy class? 
    private void btnProxy_Click(object sender, EventArgs e)
    {
        ICar car = new ProxyCar(new Driver(16));
        car.DriveCar();

        car = new ProxyCar(new Driver(25));
        car.DriveCar();
    }
}
```

# UML диаграма
[](https://en.wikipedia.org/wiki/Proxy_pattern)
