#accessor #mutator #setter #getter #this 

| string methods  | value                                   |
| --------------- | --------------------------------------- |
| `length()`      | returns the length                      |
| `concat()`      | concatenates two strings                |
| `equals()`      | checks for equality between two strings |
| `indexOf()`     | returns the index of a substring        |
| `charAt()`      | returns a character                     |
| `substring()`   | returns a substring                     |
| `toUpperCase()` | returns the upper case version          |
| `toLowerCase()` | returns the lower case version          |

Check DNA game
A protein has the following qualities:
1. It begins with a “start codon”: `ATG`.
2. It ends with a “stop codon”: `TGA`.
3. In between, each additional codon is a sequence of three nucleotides.

So for example:
- `ATGCGATACTGA` is a protein because it has the start codon `ATG`, the stop codon `TGA`, and the length is divisible by 3.
- `ATGCGATAGA` is not a protein because the sequence length is not divisible by 3, so the third condition is not satisfied.

```java
public class DNA {

	static String dna1 = "ATGCGATACGCTTGA";
	static String dna2 = "ATGCGATACGTGA";
	static String dna3 = "ATTAATATGTACTGA";
	static String dna = dna1;
	
	public static String checkProtein(String dnaInput) {
		String lastThree = dnaInput.substring(dnaInput.length() - 3,dnaInput.length());
	
	if ((dnaInput.contains("ATG")) && (lastThree.equals("TGA"))) {
		if (dnaInput.length() % 3 == 0) {
			return "This is a protein";
		} else {
			return "This is not a protein";
		}
		} else {
			return "This is not a protein";
		}
	}
	
	  
	public static void main(String[] args) {
	
		//to examine if its a legit DNA
		System.out.println("DNA1: " + checkProtein(dna1));
		System.out.println("DNA2: " + checkProtein(dna2));
		System.out.println("DNA3: " + checkProtein(dna3));
		}
}
```


**Accessor and Mutator Methods**
Mutator methods, or “setters”, often are `void` methods — they don’t return anything, they just reset the value of an existing variable. Similarly, they often have one parameter that is the same type as the variable they’re trying to change.
`Bank.java`
```java
public class Bank{

	public static void main(String[] args){
		CheckingAccount accountOne = new CheckingAccount("Zeus", 100, "1");
		CheckingAccount accountTwo = new CheckingAccount("Hades", 200, "2");
		System.out.println(accountOne.getBalance());
		// with setter, you cant use system.out.println
		accountOne.setBalance(5000);
		System.out.println(accountOne.getBalance());
	}

}
```

`CheckingAccount.java`
```java
public class CheckingAccount{

	public String name;
	private int balance;
	private String id;
	public CheckingAccount(String inputName, int inputBalance, String inputId){
		name = inputName;
		balance = inputBalance;
		id = inputId;
	}
	  
	//this is the accessor
	public int getBalance(){
		return this.balance;
	}
	//this is the setter
	public void setBalance(int newBalance){
		this.balance = newBalance;
	}
	
}
```



### THIS 
`this` keyword
```java
public class Dog{  
  public String name;  
  
  public Dog(String inputName){  
    name = inputName;  
  }  
  
  public void speakNewName(String name){  
    System.out.println("Hello, my new name is" + this.name);  
  }  
      
  public static void main(String[] args){  
    Dog a = new Dog("Fido");  
    Dog b = new Dog("Odie");  
  
    a.speakNewName("Winston");  
    // "Fido", the instance variable of Dog a is printed. "Winston" is ignored  
  
    b.speakNewName("Darla");  
    // "Odie", the instance variable of Dog b is printed. "Darla" is ignored.  
  }  
}
```

**Instance Variable**: name declared at the class level is an instance variable. Each instance of the Dog class has its own copy of this variable.
```java
public String name;
```


**Local Variable**
• **Local Variable**: name declared in the parameter of the method speakNewName is a local variable. It is only accessible within the speakNewName method.
```java
public void speakNewName(String name) {
```

**Explanation with Example**

1. **Instance Variable**:
• This is the variable defined at the class level and is associated with the object (instance) of the class.
• In your code: public String name;

2. **Local Variable**:
• This is the variable defined within a method or as a parameter to a method. Its scope is limited to the method itself.
• In your code: String name in the method speakNewName.

**this Keyword**

• The this keyword is used to refer to the instance variable when there is a naming conflict between an instance variable and a local variable.
• In the speakNewName method, this.name refers to the instance variable name of the object, while name refers to the local variable (parameter) name.

Another example of instance and local variable 
```java
public class SavingsAccount {

  // Instance variables
  public String owner;
  public double balanceDollar;
  public double balanceEuro;

  // Constructor
  public SavingsAccount(String owner, double balanceDollar) {
    this.owner = owner; // 'owner' is a local variable here, assigned to the instance variable 'this.owner'
    this.balanceDollar = balanceDollar; // 'balanceDollar' is a local variable here, assigned to the instance variable 'this.balanceDollar'
    this.balanceEuro = balanceDollar * 0.85; // Calculated and assigned to the instance variable 'balanceEuro'
  }

  // Method to add money to the balance
  public void addMoney(int amount) {
    this.balanceDollar += amount; // 'balanceDollar' is the instance variable, 'amount' is a local variable
    this.balanceEuro = this.balanceDollar * 0.85; // Recalculate the Euro balance after adding money
  }

  public static void main(String[] args) {
    SavingsAccount account = new SavingsAccount("John Doe", 1000.0);
    System.out.println("Initial Dollar Balance: " + account.balanceDollar);
    System.out.println("Initial Euro Balance: " + account.balanceEuro);

    account.addMoney(500);
    System.out.println("Updated Dollar Balance: " + account.balanceDollar);
    System.out.println("Updated Euro Balance: " + account.balanceEuro);
  }
}
```

**Understanding this and Passing the Class Instance as a Parameter**

**Class Structure**

Here’s your class with proper formatting and without the extraneous parentheses:
```java
public class myDemoClass {
  
  int demoInstanceVariable;
  
  public void methodOne() {
    // 'this' refers to the current instance of myDemoClass
    this.methodTwo(this);
  }
  
  public void methodTwo(myDemoClass a) {
    // 'a' is the instance of myDemoClass passed as a parameter
    System.out.println(a.demoInstanceVariable);
  }

  public static void main(String[] args) {
    myDemoClass demo = new myDemoClass();
    demo.demoInstanceVariable = 10; // Set instance variable
    demo.methodOne(); // This will call methodOne which in turn calls methodTwo
  }
}
```

**Explanation**

1. **Creating an Instance**:
```java
myDemoClass demo = new myDemoClass();
demo.demoInstanceVariable = 10; // Set instance variable to 10
```

2. **Calling** **methodOne**:
```java
demo.methodOne();
```
• Inside methodOne, this refers to the demo instance.
• this.methodTwo(this); calls methodTwo on the same instance, passing this (which is demo) as the argument.

3. **Inside** **methodTwo**:
```java
public void methodTwo(myDemoClass a) {
  System.out.println(a.demoInstanceVariable);
}
```

• methodTwo prints the demoInstanceVariable of the instance a, which was passed to it.
• Since a is demo, it prints 10.

**Summary**
• **this**: Refers to the current instance of the class.
• **Passing** **this**: When you pass this to another method, you are passing the current instance of the class.
• **Using** **this** **in methods**: Allows methods to call other methods within the same instance or pass the instance to other methods.

  

This approach can be useful for chaining methods, passing the current instance to other objects or methods, and maintaining clean, modular code.