<h3>Employee / EmployeeSortingApp</h3>
<h4>Employee class code</h4>

```bash
public class Employee {
	private int id;
	private String name;
	private int hours;
		
	public int getHours() {
		return hours;
	}

	public Employee() {
		this.id = 0;
		this.name = null;
		this.hours=2;
	}
	
	public Employee(int ID, String Name,int Hours) {
		this.id= ID;
		this.name=Name;
		this.hours=Hours;		
	}
	
	public String Print() {
		return("ID = "+ id + "Name = "+ name + "Hours = "+ hours + "\n");
	}	
}
```

<h4>EmployeeSortingApp class code</h4>

```bash
import java.util.Comparator;
import java.util.PriorityQueue;

public class EmployeeSortingApp {


		public static void main(String[] args) {
	        PriorityQueue<Employee> queue = new PriorityQueue<>(Comparator.comparingInt(Employee::getHours));

	        // Adding employees to the PriorityQueue
	        queue.offer(new Employee(1, "Alice", 12));
	        queue.offer(new Employee(2, "Bob", 18));
	        queue.offer(new Employee(3, "Charlie", 16));
	        queue.offer(new Employee(4, "David", 10));
	        queue.offer(new Employee(5, "Eve", 2));

	        System.out.println("Original PriorityQueue:");
	        for (Employee e : queue) {
	            System.out.println(e.Print());
	        }

	        PriorityQueue<Employee> filteredQueue = new PriorityQueue<>(Comparator.comparingInt(Employee::getHours));
	        while (!queue.isEmpty()) {
	            Employee e = queue.poll();
	            if (e.getHours() > 15) {
	                filteredQueue.offer(e);
	            }
	        }

	        System.out.println("\nFiltered PriorityQueue (Hours > 15):");
	        while (!filteredQueue.isEmpty()) {
	            System.out.println(filteredQueue.poll().Print());
	        }
	    }
}

```


----------------------------------------------------------------------------------------------------

<h3>GenericDataProcessor Question</h3>
<h4>GenericDataProcessor class code</h4>

```bash
public class GenericDataProcessor<T extends Number> {
	
	// Generic method 01
    public T findMax(T[] array) {
        T max = array[0];
        for (T element : array) {
            if (element.doubleValue() > max.doubleValue()) {
                max = element;
            }
        }
        return max;
    }

 // Generic method 02
    public T findMin(T[] array) {
        T min = array[0];
        for (T element : array) {
            if (element.doubleValue() < min.doubleValue()) {
                min = element;
            }
        }
        return min;
    }
}

class Test {
    public static void main(String[] args) {
        GenericDataProcessor<Integer> intProcessor = new GenericDataProcessor<>();
        Integer[] intArray = {10, 20, 30, 40, 50};
        System.out.println("Max of int array: " + intProcessor.findMax(intArray));
        System.out.println("Min of int array: " + intProcessor.findMin(intArray));
        
        GenericDataProcessor<Double> doubleProcessor = new GenericDataProcessor<>();
        Double[] doubleArray = {10.5, 20.7, 30.1, 40.9, 50.3};
        System.out.println("Max of double array: " + doubleProcessor.findMax(doubleArray));
        System.out.println("Min of double array: " + doubleProcessor.findMin(doubleArray));
    }
}
```

----------------------------------------------------------------------------------------------------

<h3>DemoApp / InvalidPhoneNumberDigits / InvalidPhoneNumberStart/  Question</h3>
<h4> DemoApp class code</h4>

```bash
import java.util.Scanner;

public class DemoApp {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		System.out.print("Enter a telephone number: ");
        String phoneNumber = scanner.nextLine();
        
        try {
            validatePhoneNumber(phoneNumber);
            System.out.println("Valid phone number.");
        } catch (InvalidPhoneNumberDigits | InvalidPhoneNumberStart e) {
            System.out.println(e.getMessage());
        }

        
       
        }
	 private static void validatePhoneNumber(String phoneNumber) throws InvalidPhoneNumberDigits, InvalidPhoneNumberStart {
		 if (phoneNumber.charAt(0) != '0') {
             throw new InvalidPhoneNumberStart("The phone number must start with 0.");
         }
		 
		 if (phoneNumber.length() != 10) {
             throw new InvalidPhoneNumberDigits("The phone number must have exactly 10 digits.");
         }
         
         
	}

}
```

<h4> InvalidPhoneNumberDigits class code</h4>

```bash
class InvalidPhoneNumberDigits extends Exception {
	
    public InvalidPhoneNumberDigits(String message) {
        super(message);
    }
}

```
<h4> InvalidPhoneNumberStart class code</h4>

```bash
class InvalidPhoneNumberStart extends Exception {
    public InvalidPhoneNumberStart(String message) {
        super(message);
    }
}
```
----------------------------------------------------------------------------------------------------

<h3>HashMapp</h3>
<h4>Main class code</h4>

```bash

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        // Create a HashMap to store item names and prices
        HashMap<String, Double> itemMap = new HashMap<>();

        // Prompt user to input details for 5 items
        Scanner scanner = new Scanner(System.in);
        for (int i = 0; i < 5; i++) {
            System.out.print("Enter item name: ");
            String itemName = scanner.nextLine();
            System.out.print("Enter item price: ");
            double itemPrice = scanner.nextDouble();
            scanner.nextLine(); // Consume newline left-over

            // Store the item name and price in the HashMap
            itemMap.put(itemName, itemPrice);
        }

        // Display all items in the HashMap
        System.out.println("All items in the HashMap:");
        for (Map.Entry<String, Double> entry : itemMap.entrySet()) {
            System.out.println(entry.getKey() + " $" + entry.getValue());
        }

        // Filter items in the HashMap to include only those with names that start with 'A' and have length greater than 5 characters
        HashMap<String, Double> filteredItemMap = new HashMap<>();
        for (Map.Entry<String, Double> entry : itemMap.entrySet()) {
            if (entry.getKey().startsWith("A") && entry.getKey().length() > 5) {
                filteredItemMap.put(entry.getKey(), entry.getValue());
            }
        }

        // Display the filtered HashMap elements, including the length of each item name
        System.out.println("Filtered items in the HashMap:");
        for (Map.Entry<String, Double> entry : filteredItemMap.entrySet()) {
            System.out.println(entry.getKey() + " (length: " + entry.getKey().length() + ") $" + entry.getValue());
        }
    }
}
```



