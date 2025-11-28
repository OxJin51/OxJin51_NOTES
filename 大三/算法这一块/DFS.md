# DFS

枚举的顺序：

排列：依此枚举**每个数**放在哪个**位置**

组合：依此枚举**每个位置**放哪个**数**

# 全排列、组合输出与选数问题

回溯算法是一种通过探索所有可能解来求解问题的算法，通常使用深度优先搜索（DFS）实现。其核心框架如下：

```python
def backtrack(路径, 选择列表):
    if 满足结束条件:
        结果.add(路径)
        return
    
    for 选择 in 选择列表:
        做选择
        backtrack(更新路径, 更新选择列表)
        撤销选择
```

在实际应用中，“选择列表”和“选择条件”会根据问题特点而变化。下面通过三道经典题目（全排列、组合输出、选数）总结如何确定选择列表和选择条件。

------

## 1. 全排列问题

**问题描述**：给定数字n，生成1到n的所有排列（顺序不同视为不同解）。

### 代码实现

```c++
#include<iostream>
using namespace std;
const int N = 10;
int nums[N];
bool st[N];
int n;

void dfs(int u) {
    if (u > n) {
        for (int i = 1; i <= n; i++) printf("%5d", nums[i]);
        puts("");
        return;
    }
    for (int i = 1; i <= n; i++) {
        if (!st[i]) {
            nums[u] = i;
            st[i] = true;
            dfs(u + 1);
            st[i] = false;
        }
    }
}

int main() {
    cin >> n;
    dfs(1);
    return 0;
}
```

### 选择列表与选择条件

- **选择列表**：所有数字1到n（通过循环`for (int i = 1; i <= n; i++)`生成）。
- **选择条件**：数字未被使用（通过状态数组`st`检查`!st[i]`）。
- **做选择**：将数字加入路径（`nums[u] = i`），并标记为已使用（`st[i] = true`）。
- **撤销选择**：标记数字为未使用（`st[i] = false`）。
- **递归调用**：只传递位置参数（`u + 1`），选择列表通过`st`数组隐式更新。

**关键点**：排列问题顺序重要，因此需要跟踪每个数字的使用状态，确保每个数字只使用一次。

------

## 2. 组合输出问题（P1157）

**问题描述**：从1到n中选取r个数字，输出所有组合（顺序不重要，按升序排列）。

### 代码实现

```c++
#include<iostream>
using namespace std;
const int N = 25;
int num[N];
int n, r;

void dfs(int u, int start) {
    if (u > r) {
        for (int i = 1; i <= r; i++) printf("%3d", num[i]);
        puts("");
        return;
    }
    for (int i = start; i <= n; i++) {
        num[u] = i;
        dfs(u + 1, i + 1);
        num[u] = 0; // 可选撤销
    }
}

int main() {
    cin >> n >> r;
    dfs(1, 1);
    return 0;
}
```

### 选择列表与选择条件

- **选择列表**：从当前起始位置`start`到n的数字（通过循环`for (int i = start; i <= n; i++)`生成）。
- **选择条件**：无显式条件，但通过起始位置确保数字升序（避免重复组合）。
- **做选择**：将数字加入路径（`num[u] = i`）。
- **撤销选择**：路径值重置（`num[u] = 0`，可选，因为下次覆盖）。
- **递归调用**：传递位置参数和新的起始位置（`u + 1, i + 1`），确保下次选择从当前数字之后开始。

**关键点**：组合问题顺序不重要，因此通过起始位置控制选择范围，避免生成重复组合（如[1,2]和[2,1]视为相同）。

------

## 3. 选数问题（P1036）

**问题描述**：从n个整数中选k个整数，求和为素数的组合数。

### 代码实现（优化版）

```
#include<iostream>
#include<vector>
using namespace std;
const int N = 25;
int nums[N];
int n, k;
int res;

bool isPrime(int num) {
    if (num < 2) return false;
    if (num == 2) return true;
    if (num % 2 == 0) return false;
    for (int i = 3; i * i <= num; i += 2) {
        if (num % i == 0) return false;
    }
    return true;
}

void dfs(int u, int start, int currentSum) {
    if (u > k) {
        if (isPrime(currentSum)) res++;
        return;
    }
    for (int i = start; i <= n; i++) {
        dfs(u + 1, i + 1, currentSum + nums[i]);
    }
}

int main() {
    cin >> n >> k;
    for (int i = 1; i <= n; i++) cin >> nums[i];
    dfs(1, 1, 0);
    cout << res;
    return 0;
}
```

### 选择列表与选择条件

- **选择列表**：从起始位置`start`到n的数字（循环`for (int i = start; i <= n; i++)`），数字来自输入数组`nums`。
- **选择条件**：无显式条件，但通过起始位置确保组合唯一。
- **做选择**：不显式存储路径，而是累加和（`currentSum + nums[i]`）。
- **撤销选择**：不需要显式撤销，因为和通过参数传递，路径不维护。
- **递归调用**：传递位置、新起始位置和当前和（`u + 1, i + 1, currentSum + nums[i]`）。

**关键点**：与组合问题类似，但需要计算和并检查素数。效率优化重点在素数检查（可使用更高效的算法或预处理素数表）。

------

## 总结：如何确定选择列表和选择条件

- **选择列表的生成**： 如果问题要求所有元素且顺序重要（如排列），选择列表是所有元素，但需用状态数组跟踪可用性。 如果问题要求组合且顺序不重要（如组合），选择列表是从当前起始位置到最后的元素，通过起始位置避免重复。
- **选择条件**： 排列：检查元素是否未被使用（`!st[i]`）。 组合和选数：无显式条件，但通过起始位置隐式确保升序。
- **做选择与撤销选择**： 排列：需要显式标记和取消标记状态。 组合和选数：通常不需要显式撤销路径，因为参数传递或覆盖即可。
- **递归参数**： 排列：只需传递位置参数。 组合和选数：需传递位置和起始位置，选数还需传递当前和。

通过调整选择列表和选择条件，同一回溯框架可解决多种问题。理解问题约束（如顺序是否重要、是否需要去重）是确定选择方式的关键。