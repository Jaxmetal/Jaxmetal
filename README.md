import java.util.Scanner;
public class Minecraft {
    private static final int WORLD_SIZE = 10;
    private static char[][] world = new char[WORLD_SIZE][WORLD_SIZE];
    private static int playerX = 0;
    private static int playerY = 0;
    public static void main(String[] args) {
        initializeWorld();
        Scanner scanner = new Scanner(System.in);
        while (true) {
            displayWorld();
            System.out.print("Enter your move (w-up, s-down, a-left, d-right): ");
            String move = scanner.nextLine();
            movePlayer(move);
        }
    }
    public static void initializeWorld() {
        for (int i = 0; i < WORLD_SIZE; i++) {
            for (int j = 0; j < WORLD_SIZE; j++) {
                world[i][j] = '-';
            }
        }
        world[playerY][playerX] = 'P';
    }
    public static void displayWorld() {
        for (int i = 0; i < WORLD_SIZE; i++) {
            for (int j = 0; j < WORLD_SIZE; j++) {
                System.out.print(world[i][j] + " ");
            }
            System.out.println();
        }
    }
    public static void movePlayer(String direction) {
        switch (direction) {
            case "w":
                if (playerY > 0) {
                    world[playerY][playerX] = '-';
                    playerY--;
                    world[playerY][playerX] = 'P';
                }
                break;
            case "s":
                if (playerY < WORLD_SIZE - 1) {
                    world[playerY][playerX] = '-';
                    playerY++;
                    world[playerY][playerX] = 'P';
                }
                break;
            case "a":
                if (playerX > 0) {
                    world[playerY][playerX] = '-';
                    playerX--;
                    world[playerY][playerX] = 'P';
                }
                break;
            case "d":
                if (playerX < WORLD_SIZE - 1) {
                    world[playerY][playerX] = '-';
                    playerX++;
                    world[playerY][playerX] = 'P';
                }
                break;
            default:
                System.out.println("Invalid move. Please enter w, s, a, or d.");
        }
    }
}
