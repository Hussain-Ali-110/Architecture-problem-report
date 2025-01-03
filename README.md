# Architecture-problem-report





package Presentation;

import business.UserService;
import business.ProductService;

public class MicroservicesApplication {
    public static void main(String[] args) {
        UserService userService = new UserService();
        ProductService productService = new ProductService();
        System.out.println("User Login...");
        userService.loginUser("Tahir Orakzai", "password123");
        System.out.println("Add Product...");
        productService.addProduct("Laptop", 18000.50);
    }
}

package Data;
public class ProductDAO {
    public void saveProduct(String productName, double price) {
        System.out.println("Product saved: " + productName + " ,RS" + price);
    }
}
package Data;
public class UserDAO {
    public boolean isUserValid(String username, String password) {
        return username.equals("Tahir Orakzai") && password.equals("password123");
    }
}


package business;
import Data.ProductDAO;
public class ProductService {
    private ProductDAO productDAO;
    public ProductService() {
        this.productDAO = new ProductDAO();   
    }
    public void addProduct(String productName, double price) {
        productDAO.saveProduct(productName, price);
        System.out.println("Product added: " + productName + "RS" + price);
    }
}
package business;
import Data.UserDAO;

public class UserService {
    private UserDAO userDAO;

    public UserService() {
        this.userDAO = new UserDAO();  
    }
    public void loginUser(String username, String password) {
        if (userDAO.isUserValid(username, password)) {
            System.out.println("User logged in: " + username);
        } else {
            System.out.println("Invalid credentials for user: " + username);
        }
    }
}

