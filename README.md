# TSP Dynamic Programming City Tour Planner

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Algorithm](https://img.shields.io/badge/Algorithm-TSP-blue?style=for-the-badge)
![Technique](https://img.shields.io/badge/Technique-Dynamic%20Programming-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-success?style=for-the-badge)

A sophisticated Dynamic Programming solution for the Traveling Salesman Problem (TSP) designed for optimal city tour planning. This system maximizes tourist satisfaction by considering personal interests, visitor loads, and travel constraints.

## 🏛️ Project Overview

This project implements an intelligent city tour planning system that:
- **Maximizes attractiveness scores** based on personal interests and crowd levels
- **Minimizes travel time** while visiting all landmarks exactly once
- **Uses Dynamic Programming with memoization** to avoid O(n!) complexity
- **Starts and ends at Hotel** following classic TSP constraints

## 🎯 Problem Definition

**Goal**: Plan an optimal tour route that starts and ends at a Hotel, visits all city landmarks exactly once, and maximizes the total attractiveness score while considering:

- **Base Attractiveness Score**: Initial appeal of each landmark
- **Personal Interest Factor**: Tourist's interest level (0.0 to 1.0 scale)  
- **Visitor Load Factor**: Crowd density impact (reduces attractiveness)
- **Travel Time**: Time between landmarks

**Formula**: `Final Score = Base Score × Interest Factor × (1 - Load Factor)`

## 🧠 Algorithm Approach

### Dynamic Programming with Memoization
- **Time Complexity**: O(n² × 2ⁿ) - significantly better than brute force O(n!)
- **Space Complexity**: O(n × 2ⁿ) for memoization storage
- **Technique**: State space reduction using visited landmark bitmasks

### Key Optimization Strategies
1. **Memoization Maps**: Store computed results for state (current_location, visited_set)
2. **State Representation**: Use string-based visited set representation
3. **Pruning**: Early termination when all landmarks visited

## 🔧 Implementation Details

### Core Classes and Methods

#### `PathMap` Class
- **Constructor**: `PathMap(String graphPath, String interestPath, String loadPath)`
  - Time Complexity: O(n)
  - Reads and processes all input files

- **`tsp(String current, Set<String> visited)`**
  - Time Complexity: O(n² × 2ⁿ)
  - Core recursive function with memoization

- **`findOptimalPath()`**
  - Time Complexity: O(n² × 2ⁿ)
  - Main algorithm coordinator and result presenter

### Data Structures
```java
Map<String, Map<String, Double[]>> adjacencyList    // Graph representation
Map<String, Double> personalInterest                // Interest factors
Map<String, Double> visitorLoad                     // Crowd factors  
Map<String, Map<String, Double>> storeScore         // Memoization for scores
Map<String, Map<String, String>> storePath          // Memoization for paths
```

## 📁 Input File Formats

### 1. `landmark_map_data.txt`
```
from_landmark to_landmark base_score travel_time
Hotel Park 8.5 15
Hotel Museum 7.2 20
Park Museum 6.8 10
...
```

### 2. `personal_interest.txt`  
```
landmark_name interest_factor
Park 0.9
Museum 0.7
Tower 0.8
...
```

### 3. `visitor_load.txt`
```
landmark_name load_factor
Park 0.3
Museum 0.5  
Tower 0.2
...
```

## 🚀 Usage Instructions

### Prerequisites
- Java Development Kit (JDK) 8 or higher
- Input files in `src/` directory

### Compilation and Execution
```bash
# Navigate to project directory
cd tsp-dynamic-programming-city-tour-planner

# Compile the Java file
javac src/PathMap.java

# Run the program
java -cp src PathMap
```

### Interactive Usage
```bash
Please enter the total number of landmarks (including Hotel): 4
Three input files are read.
The tour planning is now processing…
```

## 📊 Sample Output

```
The visited landmarks:
1- Hotel
2- Park  
3- Museum
4- Tower
5- Hotel

Total attractiveness score: 20.99
Total travel time: 90 minutes
```

## ⚡ Performance Analysis

### Time Complexity Breakdown
| Method | Complexity | Description |
|--------|------------|-------------|
| `fileExists()` | O(1) | File existence check |
| `readPersonalInterest()` | O(n) | Read interest file |
| `readVisitorLoad()` | O(n) | Read load file |
| `readLandmarkData()` | O(n) | Read graph file |
| `tsp()` | O(n² × 2ⁿ) | Core TSP algorithm |
| `findOptimalPath()` | O(n² × 2ⁿ) | Overall algorithm |

### Space Complexity
- **Memoization Storage**: O(n × 2ⁿ) 
- **Graph Representation**: O(n²)
- **Total Space**: O(n × 2ⁿ)

### Algorithm Efficiency
- **Without DP**: O(n!) = 5,040 operations for 7 landmarks
- **With DP**: O(n² × 2ⁿ) = 896 operations for 7 landmarks
- **Improvement**: ~82% reduction in computational complexity

## 🎨 Features

### Core Functionality
- ✅ **Dynamic Programming Optimization**: Memoization-based TSP solution
- ✅ **Multi-factor Scoring**: Personal interest + visitor load + base score
- ✅ **Path Reconstruction**: Complete tour route generation
- ✅ **Input Validation**: File existence and format checking
- ✅ **Error Handling**: Graceful handling of invalid inputs

### Advanced Features  
- 🔍 **State Space Optimization**: Efficient visited set representation
- 📊 **Comprehensive Analytics**: Score and time tracking
- 🎯 **Exact Solution Guarantee**: Optimal tour finding
- 💾 **Memory Optimization**: Efficient memoization storage

## 🏗️ Architecture

### Design Patterns
- **Strategy Pattern**: Different scoring calculation strategies
- **Memoization Pattern**: Dynamic programming optimization
- **Factory Pattern**: Array generation methods

### Code Organization
```
PathMap.java
├── Data Input Methods
│   ├── readPersonalInterest()
│   ├── readVisitorLoad()
│   └── readLandmarkData()
├── Core Algorithm
│   ├── tsp() [Recursive DP]
│   └── partition() [Helper]
├── Utility Methods
│   ├── fileExists()
│   └── getUserExpectedLandmarkCount()
└── Main Execution
    ├── findOptimalPath()
    └── main()
```

## 🧪 Testing Scenarios

### Test Cases
1. **Small Graph** (4 landmarks): Verify correctness
2. **Medium Graph** (7 landmarks): Performance validation  
3. **Edge Cases**: Single landmark, disconnected graph
4. **Load Testing**: Large datasets with performance monitoring

### Validation Methods
- **Manual Verification**: Small examples with known optimal solutions
- **Performance Benchmarking**: Time complexity validation
- **Stress Testing**: Large input handling

## 🎓 Educational Value

### Learning Objectives
- **Dynamic Programming**: Advanced optimization techniques
- **Graph Algorithms**: TSP and shortest path concepts  
- **Complexity Analysis**: Time and space efficiency
- **Real-world Applications**: Tourism and logistics optimization

### Academic Context
- **Course**: CME 2204 - Computer Engineering
- **Assignment Type**: Dynamic Programming Project
- **Skills Demonstrated**: Algorithm design, optimization, analysis

## 🤝 Contributing

### Development Setup
```bash
# Clone the repository
git clone https://github.com/iremt11/tsp-dynamic-programming-city-tour-planner.git

# Create feature branch
git checkout -b feature/your-feature-name

# Make changes and commit
git commit -m "feat: add your feature description"

# Push and create pull request
git push origin feature/your-feature-name
```

### Contribution Guidelines
- Follow Java coding conventions
- Add comprehensive comments for new methods
- Include time/space complexity analysis
- Test with sample input files
- Update documentation as needed

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Authors

**İrem** - Computer Engineering Student
- GitHub: [@iremt11](https://github.com/iremt11)

## 🙏 Acknowledgments

- **Algorithm References**: Classic TSP and Dynamic Programming literature
- **Optimization Techniques**: Memoization and state space reduction methods

---

**Note**: This implementation is part of academic coursework demonstrating advanced dynamic programming techniques for NP-hard optimization problems.
