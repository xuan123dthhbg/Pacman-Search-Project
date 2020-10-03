### PACMAN PROJECT - SEARCH ###

## Question 1: Depth First Search ##
python pacman.py -l tinyMaze -p SearchAgent
python pacman.py -l mediumMaze -p SearchAgent
python pacman.py -l bigMaze -z .5 -p SearchAgent

Mô tả: 
nodeStack - chứa các node trong quá trình duyệt DFS.

oldNode - set lưu trữ các node đã duyệt qua

currentNodeState - trạng thái của node hiện tại đang duyệt tới

move - các actions của Pacman từ vị trí ban đầu tới node hiện tại

Duyệt DFS cho đến khi nodeStack không còn phần tử nào hoặc khi đạt được tới goalState.


## Question 2: Breath First Search
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python pacman.py -l bigMaze -p SearchAgent -a fn=bfs -z .5
python eightpuzzle.py

Mô tả: 
Tương tự Question 1 nhưng ta dùng Queue thay vì Stack để duyệt BFS

## Question 3: Uniform Cost Search
python pacman.py -l mediumMaze -p SearchAgent -a fn=ucs
python pacman.py -l mediumDottedMaze -p StayEastSearchAgent
python pacman.py -l mediumScaryMaze -p StayWestSearchAgent

Mô tả: Sử dụng PriorityQueue để duyệt UCS. Các node có mức độ ưu tiên cao hơn (chi phí thấp hơn) sẽ được duyệt trước.
oldNode: 1 dict lưu trữ các node đã duyệt

Trong quá trình duyệt, nếu phát hiện cần chi phí thấp hơn để tới currentNodeState thì tiến hành gán lại chi phí cho currentNodeState trong oldNode

Duyệt UCS cho đến khi nodePriorityQueue không còn phần tử nào hoặc khi đạt được tới goalState

## Question 4: A Star Search
python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic

Mô tả: Sử dụng PriorityQueue tương tự Question 3

Công thức tính độ ưu tiên của từng node trong PriorityQueue: F = G + H

## Question 5: Corners Problem
python pacman.py -l tinyCorners -p SearchAgent -a fn=bfs,prob=CornersProblem
python pacman.py -l mediumCorners -p SearchAgent -a fn=bfs,prob=CornersProblem

Mô tả:
Tại hàm init ta lưu lại trạng thái bắt đầu của Pacman, có thể lấy bằng hàm getStartState(...). Kiểm tra Pacman khi bắt đầu đã nằm ở bất kỳ góc nào hay chưa.

isGoalState: kiểm tra Pacman đã tới tất cả các góc hay chưa và trả về True/False

getSuccessors: kiểm tra các hướng có tường hay không, cập nhật trạng thái và trả về các successors có thể đi được.

Sử dụng các thuật toán tìm kiếm đã làm ở các Question trên để giải quyết bài toán

## Question 6: Corners Problem: Heuristic
python pacman.py -l mediumCorners -p AStarCornersAgent -z 0.5

Mô tả:
findClosestPoint: Trả về node gần nhất so với node hiện tại 

findFarthesetPoint: Trả về node xa nhất so với node hiện tại

unvisitedCorner: mảng các góc chưa được đi tới

Heuristic = currentToClosest + closestToFarthest 

## Question 7: Eating all the dots
python pacman.py -l testSearch -p AStarFoodSearchAgent

Mô tả: 
foodList: list vị trí các food (dots)
Thuật toán tương tự Q6

## Question 8:  Suboptimal Search
python pacman.py -l bigSearch -p ClosestDotSearchAgent -z .5

Mô tả: Sử dụng thuật toán BFS
isGoalState: trả về trạng thái hiện tại có phải là đích đến hay không