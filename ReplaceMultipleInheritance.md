To depict MultipleInheritance kind of structure we can use has a (composition) instead of is a (inheritance).

```
interface Iprinter{
	public void print();
}

interface Iscanner{
	public void scan();
}

class Printerr implements Iprinter{
	@Override
	public void print(){
		System.out.println("printed");
	}
}



class Scanner implements Iscanner{
	@Override
	public void  scan(){
		System.out.println("scanned");
	}
}

class PrintManager {
	Iprinter printer;
	PrintManager(Iprinter printer){
		this.printer = printer;
	}
	public void print() {
		printer.print();
	}
}



class ScanManager {
	Iscanner scanner;
	ScanManager(Iscanner scanner){
		this.scanner =  scanner;
	}


	public void scan() {
		scanner.scan();

	}
}

class PrinterScanner implements Iprinter, Iscanner{
	Iprinter printer = new Printerr();
	Iscanner scanner = new Scanner();
	@Override
	public void scan() {
		// TODO Auto-generated method stub
		
	}
	@Override
	public void print() {
		// TODO Auto-generated method stub
		
	}
}

public class PrinterMain {
	public static void main(String[] args) {
		 new PrintManager(new Printerr());
		 new ScanManager(new Scanner());
		 new PrintManager(new PrinterScanner());
		 new ScanManager(new PrinterScanner());
	}
}

```

