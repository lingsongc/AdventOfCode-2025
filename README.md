# AoC-2025
My attempt at AoC 2025

Code is written in c++.

## Thought Process
### Day 1
Part 1:  
Left turn is minus, Right turn is plus. If the final dial value is below 0, add 100, if it is above, subtract 100. Check if the dial is at zero, the add to counter.

Part 2:  
Now everytime I add or subtract 100, I increase my counters since it means that the dial passed 0. Then check for double counting: If I turn left from zero, my dial will be negative and I would have to add 100, increasing counter when it is not needed. If I turn right and land on 0, i.e. dial will be 100, i will subtract 100, counting once, and since now the dial is at zero, it will be counted twice. 

### Day 2
Part 1:  
I parse the input into a vector of numbers, where every even index is the start, and odd the end of the range. I take the half prefix (rounded down for odd digits) of the starting number (1234 will be split to 12, 67890 will be split to 67) and generate possible invalid ids by splicing the prefix together (12 becomes 1212). Special consideration for single digits was added. The ids will be checked to see if they lie within the range, and the prefix will be iterated up by one. The numbers generated for 66-102 will be 66, 77, 88, 99, 1010. If the id is bigger than the range, there is no need to continue to generate.

Part 2:  
The above method will be hard to replicate for part 2. Instead, I iterate from the start to the end number, checking if each number within the range fits the pattern. The check now consist of breaking the ids into smaller same sized chunks, and checking if each chunk is the same.

### Day 3
Part 1:  
Since the digits must be in order, the last number in the line cannot be the first digit. Hence, I just need to check the first length-1 digits for the biggest number (A), then the remaining digits after A, for the next biggest number.

Part 2:  
Taking a similar approach from above. since I need 12 digits, the last 11 digits cannot be the 1st number, the last 10 digits cannot be the 2nd number and so on. Hence I just need to find the larges number in the limited range and apply the same concept on the rest of the 11 numbers.

### Day 4
Part 1:  
Treating the input like a matrix, I went through each entry, counting the number of rolls around the entry, and increasing the counter only if there is less than 4 rolls around the entry.

Part 2:
I added a new variable to keep track of how mnay rolls can be removed. While the variale is not zero, I will keep rechecking and counting based on part 1. Furthermore, I store the coordinated to those rolls that will be removed and removed them after each round. When the number of rools that can be removed is 0, it reached the end. Another counter keeps track of all the rolls removed for all the rounds.

### Day 5
Part 1:  
I parsed the range as pairs now (improvement from Day 2 I guess), checking recursively if the ids lie within the range.

Part 2:  
I tried iterating each number from every range, storing unique ids in a vector until the end and taking the size of the vector is my answer. Obviously it did not work since the numbers get very large. Instead, I merge the ranges together, simplifying the intervals. For each interval, I just need to take end-start+1.

### Day 6
Part 1:  
I parsed all the data into vectors. First vector contains lists of numbers in each row, with whitespace removed, and second vector contains all the operands, with whitespace removed. Afterwards, just combine each number from the rows together.

Part 2:  
A different approach was needed. Instead of parsing the numbers, I slowly iterated through each column, storing the number in a vector. When I reach a column of with no numbers, I will proceed to add or multiple the numbers in the vector, and adding it to the total count. A last check is needed for the last column as there is no empty column to trigger the combination.
