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
