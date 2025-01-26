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
