import java.util.*;

class Plane {
    private int ID;
    private String name;
    private int year;

    public Plane(int ID, String name, int year) {
        this.ID = ID;
        this.name = name;
        this.year = year;
    }

    public String getName() {
        return name;
    }

    public int getYear() {
        return year;
    }
}

public class Main {
    public static void main(String[] args) {
        HashSet<Plane> planes = new HashSet<>();
        for (int i = 1; i <= 100; i++) {
            Plane plane = new Plane(i, "Plane " + i, 2000 + i);
            planes.add(plane);
        }

        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Menu:");
            System.out.println("1) Sort by name");
            System.out.println("2) Sort by year of production");
            System.out.println("3) Filter by name");
            System.out.println("4) Filter by year of production");
            System.out.println("5) Filter by specified year");
            System.out.println("6) Exit");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    List<Plane> sortedByName = new ArrayList<>(planes);
                    Collections.sort(sortedByName, Comparator.comparing(Plane::getName));
                    for (Plane plane : sortedByName) {
                        System.out.println(plane.getName() + " - " + plane.getYear());
                    }
                    break;
                case 2:
                    List<Plane> sortedByYear = new ArrayList<>(planes);
                    Collections.sort(sortedByYear, Comparator.comparingInt(Plane::getYear));
                    for (Plane plane : sortedByYear) {
                        System.out.println(plane.getName() + " - " + plane.getYear());
                    }
                    break;
                case 3:
                    System.out.println("Enter search term:");
                    String searchTerm = scanner.next();
                    for (Plane plane : planes) {
                        if (plane.getName().contains(searchTerm)) {
                            System.out.println(plane.getName() + " - " + plane.getYear());
                        }
                    }
                    break;
                case 4:
                    System.out.println("Enter year of production:");
                    int year = scanner.nextInt();
                    for (Plane plane : planes) {
                        if (plane.getYear() == year) {
                            System.out.println(plane.getName() + " - " + plane.getYear());
                        }
                    }
                    break;
                case 5:
                    System.out.println("Enter specified year:");
                    int specifiedYear = scanner.nextInt();
                    for (Plane plane : planes) {
                        if (plane.getYear() == specifiedYear) {
                            System.out.println(plane.getName() + " - " + plane.getYear());
                        }
                    }
                    break;
                case 6:
                    System.out.println("Exiting program");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice, please try again");
            }
        }
    }
}


Это пример Java программы, которая создает список 100 самолетов, предоставляет меню для сортировки и фильтрации этого списка и вывода результатов в соответствии с выбором пользователя.
