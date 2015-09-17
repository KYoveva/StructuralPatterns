# Composite Pattern
## Мотивация
* Composite design pattern се използва когато се създават йерархични модели на обекта. 
Той дефинира начина по който се прави дизайна на рекурсивната дървовидната стуктура от
обекти, където индивидуалните обекти и групи могат да се достъпват.

## Цел
* Целта на този дизайн е да композира обектите в дървовидна структура която да представи
част или цялата йерархия.

## Приложение
* Позволява на клиента да третира индивидуалните обекти и компоненти по един с същи начин.

## Употреба
* Windows.Forms.Control
* System.Web.UI.Control
* System.Xml.XmlNode

## Имплементация
```c#
namespace CompositePattern
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    //Client
    class Program
    {
        static void Main(string[] args)
        {
            // initialize variables
            var compositeGraphic = new CompositeGraphic();
            var compositeGraphic1 = new CompositeGraphic();
            var compositeGraphic2 = new CompositeGraphic();

            //Add 1 Graphic to compositeGraphic1
            compositeGraphic1.Add(new Ellipse());

            //Add 2 Graphic to compositeGraphic2
            compositeGraphic2.AddRange(new Ellipse(), 
                new Ellipse());

            /*Add 1 Graphic, compositeGraphic1, and 
              compositeGraphic2 to compositeGraphic */
            compositeGraphic.AddRange(new Ellipse(), 
                compositeGraphic1, 
                compositeGraphic2);

            /*Prints the complete graphic 
            (four times the string "Ellipse").*/
            compositeGraphic.Print();
            Console.ReadLine();
        }
    }
    //Component
    public interface IGraphic
    {
        void Print();
    }
    //Leaf
    public class Ellipse : IGraphic
    {
        //Prints the graphic
    	public void Print()
        {
            Console.WriteLine("Ellipse");
        }
    }
    //Composite
    public class CompositeGraphic : IGraphic
    {
        //Collection of Graphics.
        private readonly List<IGraphic> graphics;

        //Constructor 
        public CompositeGraphic()
        {
            //initialize generic Collection(Composition)
            graphics = new List<IGraphic>();
        }
        //Adds the graphic to the composition
        public void Add(IGraphic graphic)
        {
            graphics.Add(graphic);
        }
        //Adds multiple graphics to the composition
        public void AddRange(params IGraphic[] graphic)
        {
            graphics.AddRange(graphic);
        }
        //Removes the graphic from the composition
        public void Delete(IGraphic graphic)
        {
            graphics.Remove(graphic);
        }
        //Prints the graphic.
        public void Print()
        {
            foreach (var childGraphic in graphics)
            {
                childGraphic.Print();
            }
        }
    }
}
```
##UML диаграма
![](https://upload.wikimedia.org/wikipedia/commons/5/5a/Composite_UML_class_diagram_%28fixed%29.svg)
