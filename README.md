# Gradient-Descent-Optimizer

- 👋 Hi, I’m @jakevichnis
- 👀 I’m interested in ... Optimization, coding, Ai, finance, $
- 💻 I’m currently learning ... DSA stuff, A.I. etc., I'm still in school!
- 🍻 I’m looking to collaborate on ... Anything with Ai related coding!
- 📫 How to reach me ... https://www.linkedin.com/in/jake-vichnis-053a36190/
- ⚡ Fun fact: ... as of 1/16/25 I'm still finishing up my BS in CS (w/ AI focus :P )





Overview



The Gradient Descent Optimizer is a Java-based portfolio optimization tool that uses mean-variance optimization and gradient descent to compute the optimal allocation of assets. This program is designed for individuals and organizations interested in financial portfolio management, enabling efficient calculation of expected returns, risk, and optimized weights for asset distribution.



Features

• Implements mean-variance optimization to minimize portfolio risk while maximizing returns.

• Uses gradient descent to calculate optimal asset weights with custom gradient calculation methods.

• Efficient handling of covariance matrices for portfolio risk evaluation.

• Outputs expected returns, risk metrics, and optimized portfolios for given asset data.

• Designed for flexibility and customization for further financial analysis.



Installation

1. Prerequisites

• Java Development Kit (JDK) version 8 or higher installed.

• An IDE or text editor such as IntelliJ IDEA, Eclipse, or VS Code.

• Basic understanding of Java programming and portfolio optimization concepts.

2. Clone the Repository



git clone https://github.com/yourusername/gradient-descent-optimizer.git





3. Compile the Code

Navigate to the project directory and compile the Java files:



javac *.java





4. Run the Program

Execute the program using the following command:



java Main



Usage

1. Input price snapshots or other historical data for the assets in your portfolio.

2. The program calculates:

• Expected returns based on input data.

• Covariance matrix to measure the relationships between asset returns.

• Optimized portfolio weights using gradient descent.

3. View the program’s output, which includes optimized weights, portfolio risk, and expected returns.



Example Input/Output



Input

• Asset prices over several time intervals.

Example:



Asset A: [100, 105, 110]  

Asset B: [50, 52, 54]  







Output

• Expected Returns: [5%, 4%]

• Portfolio Weights: [60% Asset A, 40% Asset B]

• Risk (Covariance): 0.01



Project Structure



GradientDescentOptimizer/

│

├── Main.java                # Entry point for the program

├── PortfolioOptimizer.java  # Core optimization logic

├── CovarianceMatrix.java    # Handles covariance matrix construction

├── GradientDescent.java     # Gradient descent implementation

├── utils/                   # Utility classes and helper functions

└── README.md                # Project documentation



Future Enhancements

• Incorporate real-time data integration using APIs.

• Add visualization of portfolio risk and return trade-offs.

• Support additional optimization algorithms (e.g., genetic algorithms).



License



"If you end up doing anything with it, just cut me in :)  "



Contributions:

-Jake Vichnis



Contributions are welcome! Feel free to open issues or submit pull requests for bug fixes and feature enhancements.

