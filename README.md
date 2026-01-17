
---

# 笔记速记（Python / C++ / 数据结构）

## Python
* python可以使用列表做栈，使用方法与c++有些许不同：
```python
stk.append(root)#等于c++的push，c++的列表是push_back
root = stk.pop()#pop等于c++的top+pop
```
* 倒序循环（注意：左闭右开）

```python
for i in range(n - 1, -1, -1):
    ...
```

* 索引-值遍历（enumerate）

```python
for i, h in enumerate(height):
    ...
# 等价于：
for i in range(len(height)):
    h = height[i]
# 只遍历值：
for h in height:
    ...
```
* //和/的区别：
```python
%取余
/真除
//整除向下取整
**幂运算
divmod（a,b）得到(c,d):(a//b,a%b)
```
* 三元表达式

```python
x = A if condition else B
```

* 负索引：最后一个元素（同样是 O(1)）

```python
height[-1]
```
*不等
```
while pa is not pb
while pa != pb
```
* 典型列表推导式循环（求和）

```python
ans = sum(min(right_max[i], left_max[i]) - height[i] for i in range(n))
```

* or 的并列
```python
if headA is None or headB is None#两个都非
if headA or headB is None#会被翻译成
if (headA) or (headB is None):

```

* 建立列表（初始化）

```python
left_max = [height[0]] + [0] * (n - 1)
```

* 对字符串循环（enumerate + start）

```python
for i, ch in enumerate("abc", start=1):
    print(i, ch)
```

* 字典/列表查询复杂度（经验结论）

  * 字典查 key：平均 O(1)
  * 列表查元素是否存在 / 字典查 value：O(n)

* 容器追加：列表 vs 集合

```python
lst.append(x)     # list：有序
st.add(x)         # set：无序且唯一
```

* 字符转整数编码

```python
ord(s[i])
```

* defaultdict(int)：不存在的 key 默认 0（并会自动创建该 key）

```python
from collections import defaultdict
cnt = defaultdict(int)
```

* heapify：把 list 原地变成“小根堆”

```python
import heapq
heapq.heapify(q)
```

* 用负号把小根堆当“大根堆”（常用技巧）

```python
import heapq

q = [(-nums[i], i) for i in range(k)]
heapq.heapify(q)

ans = [-q[0][0]]  # q[0] 是堆顶；q[0][0] 对应 -nums[i]
```

* 堆 vs sort（更准确的说法）

  * `sorted()/sort()`：O(n log n)
  * `heapq.heapify()`：O(n)
  * 但如果你要“弹出全部元素排序输出”，堆总成本也是 O(n log n)（因为 pop n 次，每次 log n）

* 双端队列 deque

```python
import collections
q = collections.deque()
```

* 判断空串 / 判断空

```python
if t == "" or s == "":
    ...

if not something:
    ...
```

* Counter 计数器

```python
from collections import Counter
need = Counter(t)
```
* 在python当中向双端队列当中压入树节点时，需要用列表来初始化队列，因为deque需要一个可迭代的对象。
```python
q = deque([root])
等价于
q = deque()
q.append(root)
如果你直接写
deque(x) 的语义是：把 x 里的每个元素依次取出来，放进队列。
deque(root)：它会尝试“遍历 root”，但 TreeNode 不是可迭代对象，所以构造阶段就报错。
同理，对于所有数据结构都是如此构造，deque list set tuple
dict需要：mp={root:1}
heapq:[priority,root)]
```
* 切片取值（左闭右开）

```python
s[start:end]
```

* Counter 的“比较”语义（A >= B：对 B 的所有键 k，都满足 A[k] >= B[k]）

* 排序（二维区间按起点）

```python
intervals.sort(key=lambda x: x[0])
```
* 定义一个函数
```python
    def reverse(self, head: ListNode, tail: ListNode):
        prev = tail.next
        p = head
        while prev != tail:
            nex = p.next
            p.next = prev
            prev = p
            p = nex

```
* 二维列表取值：最后一个子列表的下标 1 元素

```python
merged[-1][1]
```
* 二维列表建立
```python
directions=[[0,1],[1,0],[0,-1],[-1,0]]
visit = [[False]*columns for _ in range(rows)]
```
* 列表原地覆盖（保持引用不变）
vector<pair<int,int>> v;

v.push_back({1,2});      // 先构造一个临时pair，再移动/拷贝进v
v.emplace_back(1,2);     // 直接在v的末尾原地构造pair(1,2)

```python
nums[:] = new
```
* 哈希安全取值，值得注意，需要用get来安全取值，如果不用get，遇到none会报error。而c++不会。
```python
Python

d[k]：必须有，不然 KeyError

d.get(k, default)：可能没有，没就 default（不插入）

d.setdefault(k, default)：没有就插入 default 并返回（更像 C++ 的 []）

C++ unordered_map

m[k]：没有就插入默认值再返回（有副作用）

m.find(k)：只查不插入
```

* 最大公约数 gcd

```python
import math
count = math.gcd(k, n)
```
* 矩阵取横竖长度
```python
m,n=len(matrix),len(matrix[0])
```
* 遍历取值
```python
  flag_col0 = any(matrix[i][0] == 0 for i in range(m))
```

* python当中的多重赋值以及元祖交换无需像c++一样考虑tmp
```python
a, b, c, d = b, c, d, a

```
  等价于
```c++
_tmp = (b, c, d, a)
a, b, c, d = _tmp
* 判断回文，双向遍历，甚至不需要指针和循环
```python
return vals == vals[::-1]#可以关注一下这个：的位置，val[1:3:-1]代表着从位置1开始遍历到3，-1代表反向。
```

```
---


## 核心数据结构对比：List vs Heap vs Deque（如果你怕表格渲染差，就用代码块）

```text
| 特性 | 列表 (List) | 堆 (Heap) | 双端队列 (Deque) |
| --- | --- | --- | --- |
| Python 类型 | list | heapq (操作 list) | collections.deque |
| 形象比喻 | 带编号的储物柜 | 等级森严的金字塔 | 两头通的管道 |
| 底层实现 | 动态数组 | 完全二叉树 | 双向链表/块状链表实现(实现细节依版本) |
| 头部 增/删 | 慢 O(n) | 不支持直接 | 快 O(1) |
| 尾部 增/删 | 快 O(1) | push/pop O(log n) | 快 O(1) |
| 查找最值 | 遍历 O(n) | 看堆顶 O(1) | 遍历 O(n) |
| 适用场景 | 随机访问、栈 | 优先队列、TopK | 滑动窗口、队列 |
```

---

## C++

* 创建列表（vector 初始化：数量 + 初值）

```cpp
vector<long long> pre(n + 1, 0);
vector<int> ans;
```

* for 的条件用 `;` 分割,其中第一项是初始化，第二项是条件，第三项是迭代。例如：for(初始化 ; 条件 ; 迭代)
```cpp
for (int i = 0, j = n - 1; i < j; i++, j--) { ... }

```

* 变量不能重复“声明初始化”，但可以重复赋值

```cpp
int P = 0;
P = 10086;
```

* 建立列表（左右数组），二维列表，用bool初始化矩阵

```cpp
vector<int> left_max(n), right_max(n);
vector<vector<bool>> visited(rows, vector<bool>(columns))//初始值默认都是false，括号当中第一个为创建多少个元素，第二个为元素初始化的值。
```

* array 初始化与填充

```cpp
#include <array>
array<int, 26> cnt{};
cnt.fill(0);

// 等价于：
int cnt2[26] = {0};

array<int, 26> cntS{}, cntP{};
cntS.fill(0);
cntP.fill(0);
```

* 注意：`int left, right = 0, n - 1;` 不等价于你想要的写法
  需要分别写：

```cpp
int left = 0, right = n - 1;
```

* unordered_set / unordered_map 判断存在

```cpp
last.count(ch)
```
* 队列不支持 while(Q)这样的表达，只有链表可以。队列只能用Q.empty()
* 
* 且：`&&`

* 并列声明（常见写法）

```cpp
int n = (int)s.size(), m = (int)p.size();
```

* 顺序容器追加

```cpp
ans.push_back(0);
```

* Python 需要 ord，C++ 不需要：因为 C++ 的 `char` 本身就是整数（ASCII/字节值）可直接参与下标/运算

* range-for（如果要修改元素，用引用 `&`）

```cpp
for (int &x : nums) {
    // 修改 x 会影响 nums
}
```

* map/unordered_map 查询：find（避免 count 查两次）

```cpp
auto it = cnt.find(pre - k);
if (it != cnt.end()) ans += it->second;
```

* 上面等价于（但可能查两次）：

```cpp
if (cnt.count(pre - k)) ans += cnt[pre - k];
```

* 双端队列

```cpp
#include <deque>
deque<int> q;
```
* 哨兵节点,除了dummy（listnode（0））之外：
```cpp
ListNode head, *tail = &head;//head为在栈上的虚拟节点，&为取地址
```
* 优先队列（默认大根堆）

```cpp
#include <queue>
priority_queue<pair<int,int>> pq;

pq.push({nums[i], i});
ans.push_back(pq.top().first);
```
* 实现小根堆的:
```cpp
// 目的：让 priority_queue 能存“自定义元素”，并按你指定的 key 排序

struct Status {
    int val;           // key：用于排序（优先级）
    ListNode* ptr;     // payload：你真正要带着走的数据（指针/索引/对象等）

    // priority_queue 默认是“大根堆”（top 最大）
    // 把 < 反过来写，就能让它表现成“小根堆”（top 最小）
    bool operator<(const Status& rhs) const {
        return val > rhs.val;   // val 越小，越优先出现在 top()
    }
};

priority_queue<Status> q;  // q.top() 取 val 最小的 Status

// 用法：q.push({val, ptr});  // 入堆
//      auto x = q.top(); q.pop();  // 取出最小的

```

```cpp
struct Cmp {
    bool operator()(const Status& a, const Status& b) const {
        return a.val > b.val;  // 小根堆：val 小的优先
    }
};
priority_queue<Status, vector<Status>, Cmp> q;

```
* range-for（只读）

```cpp
for (const auto &x : nums) {
    // x 依次表示 nums 的每个元素
}
```

* sort + lambda 比较函数（重点：`[] () {}`）

```cpp
sort(intervals.begin(), intervals.end(),
     [](const vector<int>& a, const vector<int>& b) {
         return a[0] < b[0];
     });
```

* lambda 的 `[]` 捕获列表

  * `[]`：不捕获外部变量
  * `[&]`：按引用捕获用到的外部变量
  * `[=]`：按值捕获用到的外部变量

* 判 0：`!matrix[i][j]` 等价于 `matrix[i][j] == 0`


* 初始化一个固定不变，经常使用的小表
* 

```cpp
private:
    static constexpr int directions[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};

```

* if判定条件bool数组：判定为真或越界即进入（对于此判定的最后一个二元bool的数组）
```cpp
            if(nextrow<0||nextrow>=rows||nextcolumn<0||nextcolumn>=columns||visited[nextrow][nextcolumn]){

            }
```
* 运算左移一位，对于非负整数来说，等价于，乘2.
```cpp
subLength <<= 1;
sublength = sunlength <<1;
sublength*=2;   
```
* 遍历矩阵：
```c++
  for (const auto& row: matrix) {
            for (int element: row) {
```

* 哈希存储节点指针：
* 赋值链表：
```c++
unordered_set<ListNode*> visited; 存的是 节点指针（地址）
ListNode*temp=head;//给temp赋值表头地址，这个listnode*就是初始化的过程，第二次赋值可以不用这个前缀
```
* 链表指针移动:
``` c++
temp = temp->next
```
* 给数组加值
```c++
vector<pair<int,int>> v;

v.push_back({1,2});      // 先构造一个临时pair，再移动/拷贝进v
v.emplace_back(1,2);     // 直接在v的末尾原地构造pair(1,2)

```
* 用数字作为节点
```cpp

head = tail = new ListNode(sum % 10);

```
* 取余，取模
```cpp
carry=sum % 10；取余
carry=sum / 10; 取模
```
* 将链表堆栈：
```cpp
stack<ListNode*> stk;
//stack<T> 是标准库容器适配器（头文件 <stack>）
//这里 T 是 ListNode*，也就是“节点指针”
```

*同时更改两个变量，通过函数。但是这个函数必须返回pair或者tuple
```cpp
  // 这里是 C++17 的写法，也可以写成
            // pair<ListNode*, ListNode*> result = myReverse(head, tail);
            // head = result.first;
            // tail = result.second;
            tie(head, tail) = myReverse(head, tail);

//函数需要这样的
 pair<ListNode*,ListNode*>reverse1(ListNode*head,ListNode*tail){
        ListNode*xinweiba=tail->next;
        ListNode*xinnaodai=head;
        while(xinweiba!=tail){
            ListNode*yucun=xinnaodai->next;
            xinnaodai->next=xinweiba;
            xinweiba=xinnaodai;
            xinnaodai=yucun;
        }
        return {tail,head};

```
* 一个典型的指针类型函数：
```cpp
Node* copyRandomList(Node* head)//第一个node*指的是输出为指针类型，指针就是地址。如果去掉星号的就是节点对象，实体节点的意思。括号当中的是输入。
本题用Node是因为题目给的就是Node
```
---

## 数据结构（概念速记）

* 普通列表：按顺序存，随机访问快（O(1)），插头删头慢（O(n)）

* 堆/优先队列：

  * 看堆顶最值：O(1)
  * push/pop：O(log n)
  * 目的就是“快速取最值”，**不擅长删除任意位置元素**

* Python 的 heapq：小根堆（最小在堆顶）

* C++ 写函数要注明返回类型

```cpp
bool is_covered(int cnt_s[], int cnt_t[]) {
    ...
}
```
*
* ASCII 计数表（0~127 直接下标计数）

```cpp
int cnt_s[128]{};
int cnt_t[128]{};
```

* C++ 三元表达式（常用于返回空串）

```cpp
return ans_left < 0 ? "" : s.substr(ans_left, ans_right - ans_left + 1);
```
* 加值对比：
Python list：append / extend
↔ C++ vector：push_back/emplace_back / insert(end, begin, end)
Python set：add / update
↔ C++ set/unordered_set：insert(x) / insert(begin, end)

---

