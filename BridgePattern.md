# Bridge pattern (Structural software design pattern)

The bridge pattern is a design pattern used in software engineering that is meant to "decouple an abstraction from its implementation so that the two can vary independently".

The Bridge Pattern allows you to vary the implementation and the abstraction by placing the two in separate class hierarchies.

- Avoide class proliferation
- Decouples an implementation so that it is not bound
permanently to an interface.
- Abstraction and implementation can be extended
independently
- Changes to the concrete abstraction classes don’t
affect the client.

![alt text](Bridge.png)

![alt text](Bridge_Design_Pattern_UML.jpg)

```
package testttt;

import java.util.ArrayList;

interface IEmailprotocol {
	public void protocolType();
}

class OldEmailProtocol implements IEmailprotocol{

	@Override
	public void protocolType() {
		System.out.println("OldEmailProtocol");
	}

}

class NewEmailProtocol implements IEmailprotocol{

	@Override
	public void protocolType() {
		System.out.println("NewEmailProtocol");
	}

}

interface IEmailSecurity {
	public void OsSecurityType();
}

class OSSecurity implements IEmailSecurity{

	@Override
	public void OsSecurityType() {
		System.out.println("OSSecurity");
	}

}

class OSXSecurity implements IEmailSecurity{

	@Override
	public void OsSecurityType() {
		System.out.println("OSXSecurity");
	}

}

abstract class IOperatingSystem {
	IEmailprotocol protocol;
	IEmailSecurity security;

	IOperatingSystem(IEmailprotocol protocol, IEmailSecurity security){
		this.protocol = protocol;
		this.security = security;
	}
	abstract void getOsInfo();
}

class MacOs extends IOperatingSystem{

	MacOs(IEmailprotocol protocol, IEmailSecurity security) {
		super(protocol, security);
	}

	@Override
	public void getOsInfo() {
		System.out.println("Mac");
		protocol.protocolType();
		security.OsSecurityType();
	}
}

class DOSOs extends IOperatingSystem{

	DOSOs(IEmailprotocol protocol, IEmailSecurity security) {
		super(protocol, security);
	}

	@Override
	public void getOsInfo() {
		System.out.println("DOS");
		protocol.protocolType();
		security.OsSecurityType();
	}
}

public class EmailExample {
	public static void main(String[] args) {
		IOperatingSystem os = new MacOs(new OldEmailProtocol(), new OSSecurity());
		os.getOsInfo();

		System.out.println();

		os = new MacOs(new NewEmailProtocol(), new OSXSecurity());
		os.getOsInfo();
	}
}
```

