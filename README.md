public class Main {
    public static void main(String[] args) {

        ProductManager productManager = new ProductManager();
        ManagementSystem managementSystem = new ManagementSystem(productManager);

        Product product1 = new Product(555, "Phone", 1500.0, 84);
        Product product2 = new Product(888, "paper", 50.0, 0);
        Product product3 = new Product(111, "Headphones", 700.0, 50);

        productManager.addProduct(product1);
        productManager.addProduct(product2);
        productManager.addProduct(product3);

        System.out.println(" Product List:");
        managementSystem.displayProducts();

        Discount discounts;
        discounts = new Discount(0.20);
        productManager.applyDiscounts(111, discounts);

        System.out.println("\nUpdated Product List (Product LIst With Discount):");
        managementSystem.displayProducts();
    }
}
public class Main {
    public static void main(String[] args) {

        ProductManager productManager = new ProductManager();
        ManagementSystem managementSystem = new ManagementSystem(productManager);

        Product product1 = new Product(555, "Phone", 1500.0, 84);
        Product product2 = new Product(888, "paper", 50.0, 0);
        Product product3 = new Product(111, "Headphones", 700.0, 50);

        productManager.addProduct(product1);
        productManager.addProduct(product2);
        productManager.addProduct(product3);

        System.out.println(" Product List:");
        managementSystem.displayProducts();

        Discount discounts;
        discounts = new Discount(0.20);
        productManager.applyDiscounts(111, discounts);

        System.out.println("\nUpdated Product List (Product LIst With Discount):");
        managementSystem.displayProducts();
    }
}
 public class Discount implements Discounts {
        private double discountPercent;

        public Discount(double discountPercent) {
            this.discountPercent = discountPercent;
        }

        public double getDiscountPercent() {
            return discountPercent;
        }

        @Override
        public double applyDiscount(double price) {
            return price * (1 - discountPercent);
        }
    }
public interface Discounts {
    double applyDiscount(double price);

}

import java.util.ArrayList;
import java.util.List;

public class ProductManager {
    private List<Product> products;

    public ProductManager() {
        products = new ArrayList<>();
    }

    public void addProduct(Product product) {
        products.add(product);
    }

    public void displayProducts() {
        if (products.isEmpty()) {
            System.out.println(" We are out of product.");
        } else {
            for (Product product : products) {
                product.displayProduct();
            }
        }
    }

    public void applyDiscounts(int productId, Discounts discount) {
        for (Product product : products) {
            if (product.getId() == productId) {
                double newPrice = discount.applyDiscount(product.getPrice());
                product.setPrice(newPrice);
                System.out.println("Discount applied successfully! ");
                return;
            }
        }
        System.out.println("Product is not found.");
    }
}
public class ManagementSystem {
    private ProductManager productManager;

    public ManagementSystem(ProductManager productManager) {
        this.productManager = productManager;
    }

    public void displayProducts() {
        System.out.println("Product List:");
        productManager.displayProducts();
    }
}
