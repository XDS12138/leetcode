# Python
* 倒序循环：for i in range(n-1,-1,-1):，但是要注意的是，第一个数值为扫描起始点，区间依然是python左闭右开，此时的-1依然是则右边的开区间。
* 索引-值遍历循环:for i,h in enumerate(height):其等价于 for i in range(len(height)):h = height[i],如果只需要遍历其中的值，那就 for h in height.
* 三元表达式：x= A if condition else B
* height[-1],这里的-1指的是列表当中最后一个元素，略微增加运算时间。
* 一个典型的列表循环：ans=sum(min(right_max[i],left_max[i])- height[i] for i in range(n))
* 建立列表 left_max=[height[0]]+[0]*(n-1)
* 对字符串进行循环：for i, ch in enumerate("abc", start=1):
    print(i, ch)
* #字典查询key是O1的复杂度，列表和字典查询value都是On的复杂度。
* #字典是见到一个存储一个，如果是列表的话，初始化会将整个列表初始化为最大的存储。
* 列表（有序）用append 集合（无序唯一）用add
* 将字符创转化为整数编码：ord(s[i]
* cnt = defaultdict(int) 的意思是：这是一个字典，但“默认值是 0”。也就是说，你访问一个不存在的 key：defaultdict(int) 会自动返回 0，并且（通常）把这个 key 建出来。普通字典 {} 访问不存在 key 会直接 KeyError
* heapq.heapify(q)#小堆顶，将列表转化成堆，python是小根堆，小的在堆顶，于是可以使用这个技巧
*       q=[(-nums[i],i) for i in range(k)]
        heapq.heapify(q)

        ans=[-q[0][0]]#注意这里的q[0]的意思是取堆顶的第一个元素的数据，q[0][0]第二个0的意思是取该数据当中的第0项，在本代码当中代指nums[i]。而第1项则为i
        #因为python当中的堆是小根堆，如果想要实现大根堆的效果，就是用两个负号。
* 堆和sort的区别在于，堆是二叉树排序，返回堆，sort时间复杂度要$O(N \log N)$，而堆$O(N)$ (线性时间，更快)
* 双端队列：q = collections.deque()#collection是一个包
* 判断空串：if t == "" or s == "":
* 判断空：if not 。。。
* 计数器：need = Counter(t)
    return ""
* 切片取值：s[start : end]
* Counter 在 Python 里支持比较：A >= B 的语义是：对 B 中所有键 k，都满足 A[k] >= B[k]
* 排序：intervals.sort(key=lambda x: x[0])#将intervals这个二维列表按每个区间的起点从小到大排序。
* 二维列表查询：merge[-1][1]#即二维列表当中最后一个列表当中的下标为1的元素
* 列表覆盖：nums[:]=new，时间复杂度O(n)
* 取公约数：count = math.gcd(k, n)
* 

* ### 核心数据结构对比：List vs Heap vs Deque

| 特性 | **列表 (List)** | **堆 (Heap)** | **双端队列 (Deque)** |
| :--- | :--- | :--- | :--- |
| **Python 类型** | `list` | `heapq` (操作 list) | `collections.deque` |
| **形象比喻** | **带有编号的储物柜** | **等级严森的金字塔** | **两头通的管道** |
| **底层实现** | 动态数组 (Array) | 完全二叉树 | 双向链表 |
| **头部** 增/删 | **最慢** O(N) | 不支持直接操作 | **极快** O(1) |
| **尾部** 增/删 | **极快** O(1) | 慢 O(log N) | **极快** O(1) |
| **查找最值** | 慢 O(N) (需遍历) | **极快** O(1) (堆顶) | 慢 O(N) |
| **适用场景** | 随机访问、栈(Stack) | 优先队列、Top K 问题 | 滑动窗口、队列(Queue) |

# C++
* 创建列表：vector<long long>pre(n+1，0)；第一个是数量，第二个是填入的值,vector<int>ans
* for的条件用了；分割
* 不能重复初始化一个变量，但是可以重复赋值，比如，int P=0后只能用P=10086
* 建立列表， vector<int> left_max(n), right_max(n);
* 列表初始化：array<int,26>cnt{};cnt.fill(0);//将二十六个元素初始化为0，等价于int cnt[26] ={0};        array<int,26>cntS{},cntP{}; cntS.fill(0);cntP.fill(0); 
* c++不能int left,right=0,n-1
* 存在：last.count(ch)
* 且：&&
* c++的并列 int n = (int)s.size(), m = (int)p.size();
* 顺序容器追加元素：ans.push_back(0);//追加元素0
* py当中需要ord，但是c++不需要呢；
* 循环：for(int x:nums){}
* 查询 auto it = cnt.find(pre-k);//找不到就返回end 。/////  if(it!=cnt.end())ans+=it->second;//找到了就将对应的次数加到ans里，也就是其value，我们刚才建立的cnt的第一位是前缀值
* 上边的这个查询等效于if (cnt.count(pre - k)) ans += cnt[pre - k];只是这个查询要查两次，使用find查询一次即可，直接取值了
* 双端队列deque<int>q;
* 优先队列，根堆priority_queue<pair<int,int>> pq
* 压入两个变量，pq.push({nums[i],i});ans.push_back(pq.top().first);
* 循环： for (const auto &x : nums) {
    // x 依次表示 nums 里的每个元素} 等价于for (int i = 0; i < nums.size(); i++) {
    int x = nums[i];
}
* 排序函数:sort(起始迭代器，结束迭代器，比较函数）;例如：sort(intervals.begin(), intervals.end(),
     [](const vector<int>& a, const vector<int>& b) {//[](){}这是lambda的表达式，临时写一个比较函数。即比较函数会拿到两个元素，两个const vector<int>，第一个是&a，第一个是&b，然后返回的是比较规则，意思就是按元素的第一个值进行排序
         return a[0] < b[0];
     });
* []的含义是捕获列表，意味着该lambda不抓任何外部变量，[&]表示把外部用的变量按引用都住进来。[=]把外部用到的变量按值复制进来
  


# 数据结构
* 普通列表和堆的区别，普通列表按顺序存，按顺序遍历。
* 堆（优先队列）取最大最小值速度极快（）O1），动态加入或弹出元素（logn），但优先队列无法制定删除其中任意一个元素，只维护进出顺序这一种要求。其目的只是为了取最值。
* python的优先队列是由小到大的
* 布尔运算逻辑函数；bool is_covered(int cnt_s[], int cnt_t[])//在 C++ 里写函数时必须说明“返回什么类型”
* 创建计数表int cnt_s[128]{};
* 三元表达式：  return ans_left < 0 ? "" : s.substr(ans_left, ans_right - ans_left + 1);
int cnt_t[128]{};
开一个能用0-127访问的技术表，常见的ascii码都在范围内，于是可直接使用这些字符串当下标计数，'A'
