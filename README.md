# Solid Principles
It is about **Readable**, **Testable**, **Extensible**, **Maintainable**<br />
**Readable** code is clear and easy to understand. <br />
Each subclass is independently **testable**. Test-cases are no longer tightly coupled.<br />
Easily **expanded or modified** to accommodate new features or requirements without breaking existing features and application flow.<br />
Easy to find and fix bugs, to add new features, and to change existing features. It helps to reduce the cost of software development and **maintenance**.<br /><br />

* **Single responsibility**: A class should have only one responsibility. This means that a class should only do one thing and do it well.<br />
**Wrong Practice:**
```java
public class Student  {  
 pubic void calculatePercentage(){  //functionality of the method  }  
 public void addStudent() {  //functionality of the method  }  
}
```
**Correct Practice:**
```java
public class Student {
 public void addStudent(){//functionality of the method}
}
public class Percentage {  
 public void calculatePercentage(){ //functionality of the method }
}  
```
* **Open-closed**: Class should be open for extension but closed for modification. Add new features to a class without modifying the existing code.

**Wrong Practice:**
```java
public class VehicleInfo {  
public double vehicleNumber(Vehicle vcl) {  
 if (vcl instanceof Car)  {  return vcl.getNumber(); } 
 if (vcl instanceof Bike)  {  return vcl.getNumber();  }  
}
```
**Correct Practice:**

```java
public abstract class VehicleInfo {
 public abstract double vehicleNumber();
}
public class Car extends VehicleInfo {
 public double vehicleNumber() {
 return this.getValue();   }
}
public class Truck extends VehicleInfo {
 public double vehicleNumber() {
 return this.getValue();   }
}
```
* **Liskov substitution**: Subclasses should be substitutable for their base classes. Functionality that works with parent class must work with child classes.<br />
**Wrong Practice:**
```java
public abstract class Bird{
    public abstract void fly();
}
public class Sparrow extends Bird{}
```
The sparrow can fly because it is a bird, but what about this:
```java
public class Duck extends Bird{}
```
Duck is a bird, but it can't fly, Duck class is a subtype of class Bird, but it shouldn't be able to use the fly method, which means we are breaking the LSP principle.

**Correct Practice:**
```java
public class Bird {
	void drinkWater() {
		System.out.println("Drink Water");
	}
}
public abstract class FlyingBird extends Bird {
	abstract void fly();
}
public class Sparrow extends FlyingBird {
	@Override
	void fly() {
		System.out.println("Low Fly Zone");
	}
}
public class Eagle extends FlyingBird{
	@Override
	void fly() {
		System.out.println("High Fly zone");
	}
} 
public class Duck extends Bird{	
}
public class BirdExample {
	public static void main(String[] args) {
		Sparrow spr = new Sparrow();
		Eagle eg = new Eagle();
		Duck dk = new Duck();
		spr.fly();
		spr.drinkWater();
		eg.fly();
		eg.drinkWater();
		dk.drinkWater();
	}
}
```
* **Interface segregation**: Clients should not be forced to depend on interfaces that they do not use. Not implement an interface that it does not need.<br />
**Wrong Practice:**
```java
public interface Conversion  {  
 public void intToDouble();  
 public void intToChar();  
 public void charToString();  
}
**Correct Practice:**
```java
public interface ConvertIntToDouble{
  public void intToDouble();
}
public interface ConvertIntToChar{
  public void intToChar();
}
public interface ConvertCharToString{
  public void charToString();
}
```
* **Dependency inversion**: High-level modules should not depend on low-level modules. Both should depend on abstractions.<br />
**Wrong Practice:**
```java
class LightBulb {
	public void turnOn() {
		System.out.println("LightBulb: Bulb turned on...");
	}	
}
class Fan {
	public void turnOn() {
		System.out.println("Fan: Fan turned on...");
	}
}
class ElectricPowerSwitch {
	public LightBulb lightBulb;
	public Fan fn;
	boolean bFlag;
	public ElectricPowerSwitch(LightBulb lightBulb) {
		this.lightBulb = lightBulb;
		bFlag = true;
	}
	public ElectricPowerSwitch(Fan fn) {
		this.fn = fn;
		bFlag = false;
	}
	public void press() {
		if (bFlag)
			lightBulb.turnOn();
		else
			fn.turnOn();
	}
}
public class ClientTest {
	public static void main(String[] args) {
		LightBulb lgt = new LightBulb();
		ElectricPowerSwitch elecBulb = new ElectricPowerSwitch(lgt);
		Fan fn = new Fan();
		ElectricPowerSwitch elecFan = new ElectricPowerSwitch(fn);
elecFan.press();
	}
}
```
**Correct Practice:**
```java
interface Switch {
	public void turnOn();
}

class LightBulb implements Switch {
	public void turnOn() {
		System.out.println("LightBulb: Bulb turned on...");
	}	
}
class Fan implements Switch {
	public void turnOn() {
		System.out.println("Fan: Fan turned on...");
	}	
}
class ElectricPowerSwitch {
	Switch swtch;
	public ElectricPowerSwitch(Switch swtch) {
		this.swtch = swtch;
	}
public void press() {
		swtch.turnOn();
	}
}
public class ClientTest {
	public static void main(String[] args) {
		Switch lgt = new LightBulb();
		ElectricPowerSwitch elecBulb = new ElectricPowerSwitch(lgt);
		elecBulb.press();
		Switch fn = new Fan();
		ElectricPowerSwitch elecFan = new ElectricPowerSwitch(fn);
		elecFan.swtch.turnOn();
	}
}
```
### More principles <br />
* **DRY** (Don’t Repeat Yourself) Principle advises avoiding duplicating code to improve maintenance, readability, and efficiency. <br />
E.g. - Create common method for all classes to checking the Empty/Null values or conversions logic or validations in utility class.<br />
* **KISS** (Keep It Super Simple) Principle - suggests prioritizing simplicity in design to enhance clarity, minimize complexity.<br />
