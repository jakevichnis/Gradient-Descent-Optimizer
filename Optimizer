import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;

// Defining main class to hold all aspects of method utilization 
public class Portfolio_Optimizer_5 {
    
    public Portfolio_Optimizer_5() {
        // initializing arrays
        this.pricePoints = new ArrayList<>();
        this.assetName = new ArrayList<>();
    }

    // this is the list to hold price points
    public ArrayList<Double> pricePoints;
    
    // this is the list to hold names of assets
    public ArrayList<String> assetName;

    // method to return an asset name assigned to the counter
    public ArrayList<String> getAssetName(int assetCounter) {
        return assetName;
    }
    
    // method to add a name of an asset to the asset name list
    public void addAssetName(String name) {
        assetName.add(name);
    }
  
    // method to add a price point of an asset to that asset's array list
    public void addPricePoint(double price) {
        pricePoints.add(price);
    }

    // method to return all price points from an asset
    public ArrayList<Double> getPricePoints() {
        return pricePoints;
    }

    

    // possible redundant method to get the average value of an asset over it's price points
    public double averageValue() {
        double averageValue = (pricePoints.get(0) + pricePoints.get(1) + pricePoints.get(2) + pricePoints.get(3) + pricePoints.get(4)) / 5.0;
        return averageValue;
    }


    // Method to calculate pure returns based on price points
    public ArrayList<Double> calculateReturns() {
        ArrayList<Double> assetReturns = new ArrayList<>();

        for (int i = 1; i < pricePoints.size(); i++) {
            double returnRate = (pricePoints.get(i) - pricePoints.get(i - 1)) / pricePoints.get(i - 1);
                assetReturns.add(returnRate);
            }
            return assetReturns;
    }


    // Helper method to calculate mean
    public double mean(ArrayList<Double> asset) {
        double sum = 0.0;
        for (double price : asset) {
            sum += price;
        }
        return sum / asset.size();
    }


    // Covariance method for two assets, returning the relationship between the average returns of two assets
    public double coVariance(ArrayList<Double> asset1, ArrayList<Double> asset2) {
        int size = asset1.size();
        double mean1 = mean(asset1);
        double mean2 = mean(asset2);
        double covariance = 0.0;
        
        for (int i = 0; i < size; i++) {
            covariance += (asset1.get(i) - mean1) * (asset2.get(i) - mean2);
        }
        
        return covariance / (size - 1);  // Use size - 1 for sample covariance
    }

        // Possible Variance method for a single asset
    public double variance(ArrayList<Double> asset) {
        int size = asset.size();
        double mean = mean(asset);
        double variance = 0.0;
        
        for (int i = 0; i < size; i++) {
            variance += (asset.get(i) - mean) * (asset.get(i) - mean);
        }
        
        return variance / (size - 1);  // Use size - 1 for sample variance
    }

        // Method to dynamically calculate & generate the covariance matrix between assets
    public static ArrayList<ArrayList<Double>> buildCovarianceMatrix(ArrayList<Portfolio_Optimizer_5> assets) {
        int n = assets.size();
        ArrayList<ArrayList<Double>> covarianceMatrix = new ArrayList<>();

        // Iterate through each pair of assets to calculate covariance
        for (int i = 0; i < n; i++) {
            ArrayList<Double> row = new ArrayList<>();
            for (int j = 0; j < n; j++) {
                double cov;
                if (i == j) {
                    // Variance for the same asset (diagonal element)
                    cov = assets.get(i).coVariance(assets.get(i).calculateReturns(), assets.get(j).calculateReturns());
                } else {
                    // Covariance between different assets (off-diagonal elements)
                    cov = assets.get(i).coVariance(assets.get(i).getPricePoints(), assets.get(j).getPricePoints());
                }
                row.add(cov);
            }
            covarianceMatrix.add(row);
        }

        return covarianceMatrix;
    }
    


        // Mean-variance optimization method
    public ArrayList<Double> weightOptimization(ArrayList<Double> expectedReturns, ArrayList<ArrayList<Double>> covarianceMatrix) {
        int n = expectedReturns.size();
        int m = covarianceMatrix.size();

        // Convert covarianceMatrix from ArrayList to 2D array for better performance
        double[][] covarianceArray = new double[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                covarianceArray[i][j] = covarianceMatrix.get(i).get(j);
            }
        }
        
    
        // Create and initialize weights to be fed into weight optimization algorithm 
        double[] weights = new double[n];
        Arrays.fill(weights, 1.0 / n);
    
        // Simple gradient descent parameters
        double learningRate = 0.01;
        int iterations = 1000;
            
        // gradient descent algorithm to generate weights 
        // iterating function to normalize weights that are then added into the optimal weights ArrayList
        for (int iter = 0; iter < iterations; iter++) {
            double[] gradient = computeGradient(weights, covarianceArray, expectedReturns);
            for (int i = 0; i < n; i++) {
                weights[i] -= learningRate * gradient[i];
            }
            normalizeWeights(weights);
        }
    
        // Convert weights to ArrayList
        ArrayList<Double> optimalWeights = new ArrayList<>();
        for (double weight : weights) {
            optimalWeights.add(weight);
        }
        // gradient descent optimization algorithm ends here, returning the weights this program will output into a further model for predictive value or decision
        return optimalWeights;
    }
    
        // method of computation to generate gradient into array for further weight learning computation, this will feed into the normalization function method (seen above)
        private double[] computeGradient(double[] weights, double[][] covarianceMatrix, ArrayList<Double> expectedReturns) {
            int n = weights.length;
            double[] gradient = new double[n];
            double[] expectedReturnsArray = new double[n];
            for (int i = 0; i < n; i++) {
                expectedReturnsArray[i] = expectedReturns.get(i);
            }
    
            // Compute the gradient as 2 * covarianceMatrix * weights - expectedReturns
            for (int i = 0; i < n; i++) {
                gradient[i] = -expectedReturnsArray[i];
                for (int j = 0; j < n; j++) {
                    gradient[i] += 2 * covarianceMatrix[i][j] * weights[j];
                }
            }
    
            return gradient;
        }
    
        // method to normalize weight data
        private void normalizeWeights(double[] weights) {
            double sum = 0.0;
            for (double weight : weights) {
                sum += weight;
            }
            for (int i = 0; i < weights.length; i++) {
                weights[i] /= sum;
            }
        }
        
// where the main program will execute using defined methods written above
public static void main(String[] args) {

            // Dynamic array of asset objects the user will define
            ArrayList<Portfolio_Optimizer_5> assets = new ArrayList<>();
            int assetCounter = 1;
        
            // Create a Scanner object to be able to take user input
            Scanner scanner = new Scanner(System.in);
        
            // Main menu loop
            while (true) {
                System.out.println("\nWelcome to Portfolio Optimizer.");
                System.out.println("This program collects 5 assets and 5 price points in linear time.\n");
        
                // Loop to collect up to 5 assets
                for (int i = 0; i < 5; i++) {
                    Portfolio_Optimizer_5 asset = new Portfolio_Optimizer_5();
        
                    // Collect asset name
                    System.out.print("Enter a name for asset_" + assetCounter + ": ");
                    String assetName = scanner.next();
                    asset.addAssetName(assetName);
        
                    // Collect 5 price points for the asset
                    for (int j = 0; j < 5; j++) {
                        System.out.print("Now input price point " + (j + 1) + " for " + asset.getAssetName(j + 1) + ": $");
                        try {
                            double price = Double.parseDouble(scanner.next());
                            asset.addPricePoint(price);
                        } catch (NumberFormatException e) {
                            System.out.println("Please enter a valid number.");
                            j--; // Repeat this iteration
                        }
                    }
        
                    // adds individual asset into list of assets instance object
                    assets.add(asset);
                    // increments the count of added assets, during looping will dictate each asset by number
                    assetCounter++;
        
                    // Ask user if they want to add another asset
                    System.out.print("Add another asset? (yes/no): ");
                    // early program termination option for user, may result in error if inputted assets are less than 4
                    String continueInput = scanner.next();
                    if (continueInput.equalsIgnoreCase("no")) {
                        break;
                    }
                }
        
                // Display all assets and their price points
                System.out.println("\nAll assets and their price points: ");
                // "for each instance of an asset among the assets..."
                for (Portfolio_Optimizer_5 asset : assets) {
                    // print the current assets to the screen/user
                    System.out.println(asset.getAssetName(assetCounter) + ": " + asset.getPricePoints());
                }
                System.out.println("\n");
                // Ask user if they want to optimize the assets
                System.out.print("Optimize each asset according to listed price points? (yes/no): ");
                System.out.println("\n");
                String decision = scanner.next();
        
                if (decision.equalsIgnoreCase("yes")) {
                    // Create a matrix to hold returns, more of a placeholder
                    ArrayList<ArrayList<Double>> returnMatrix = new ArrayList<>();
                    
                    for (Portfolio_Optimizer_5 asset : assets) {
                        // Calculate and store returns
                        ArrayList<Double> returns = asset.calculateReturns();
                        returnMatrix.add(returns);
                        System.out.println(asset.getAssetName(assetCounter) + " returns: " + returns);
        
                        // Calculate and display average value
                        double assetAverage = asset.averageValue();
                        System.out.println("Asset Average Value: " + assetAverage);

                        // Calculate and display asset variance
                        System.out.println("Variance: " + asset.variance(returns));
        
                    }
        
                    // Build covariance matrix in an arraylist within an arraylist, but this will be converted to an array in the method itself
                    ArrayList<ArrayList<Double>> covMatrix = buildCovarianceMatrix(assets);
        
                    // Display the covariance matrix optimization
                    System.out.println("Covariance Matrix: " + covMatrix);
        
                    // Perform optimization (e.g., mean-variance)
                    for (Portfolio_Optimizer_5 asset : assets) {
                        ArrayList<Double> optimizedWeights = asset.weightOptimization(asset.calculateReturns(), covMatrix);
                        System.out.println("Optimized Weights for " + asset.getAssetName(assetCounter) + ": " + optimizedWeights);
                    }
                }
                // closes the user-input reading scanner object before closing program
                scanner.close();

            }
        }
    }
