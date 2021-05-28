# Observer pattern (Behavioral software design pattern)

The observer pattern is a behavioral software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

Defines a one-to-many dependency between objects so that when one object changes state, all of its dependents are notified and updated automatically.

- Asking continuously to check for changes is bad idea
- On change notify all the subscribers  
- One to many relationship is observed  

![alt text](Observer_Design_Pattern_UML.jpg)

```
package Observer;

interface IObservable{
	public void add(IObserver o);
	public void remove(IObserver o);
	public void notify();

}

class WeatherStation implements IObservable{
	ArrayList<IObserver> list = new ArrayList<IObserver>();
	private double temprature;

	public void add(IObserver o){
		list.add(o);
	}
	public void remove(IObserver o){
		list.remove(o);
	}
	
	public void setTemprature(double temprature){
		this.temprature = temprature;
		notify();
	}

	public double getTemprature(){
		return temprature;
	}

	public void notify(){
		for(IObserver o : ArrayList){
			o.update();
		}
	}
}

interface IObserver{
	public void update();

}

class PhoneDisplay implements IObserver{
	WeatherStation weatherStation;
	PhoneDisplay(WeatherStation weatherStation){
		this.weatherStation = weatherStation;
	}
	public void update(){
		weatherStation.getTemprature();

	}
}

public class UpdateWether {
	public static void main(String[] args) {
		WeatherStation weatherStation = new WeatherStation();
		PhoneDisplay phoneDisplay = new PhoneDisplay(weatherStation);
		weatherStation.add(phoneDisplay);
		weatherStation.setTemprature(25.0);
		
	}

}


```

