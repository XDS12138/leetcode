# Python
* 倒序循环：for i in range(n-1,-1,-1):，但是要注意的是，第一个数值为扫描起始点，区间依然是python左闭右开，此时的-1依然是则右边的开区间。
* 索引-值遍历循环:for i,h in enumerate(height):其等价于 for i in range(len(height)):
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

        ans=[-q[0][0]]
        #因为python当中的堆是小根堆，如果想要实现大根堆的效果，就是用两个负号。
* 堆和sort的区别在于，堆是二叉树排序，返回堆，sort时间复杂度要$O(N \log N)$，而堆$O(N)$ (线性时间，更快)
* 
# C++
* 创建列表：vector<long long>pre(n+1，0)；第一个是数量，第二个是填入的值
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


# 数据结构
* 普通列表和堆的区别，普通列表按顺序存，按顺序遍历。
* 堆（优先队列）取最大最小值速度极快（）O1），动态加入或弹出元素（logn），但优先队列无法制定删除其中任意一个元素，只维护进出顺序这一种要求。其目的只是为了取最值。
* python的优先队列是由小到大的
