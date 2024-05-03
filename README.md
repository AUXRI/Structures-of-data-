# Structures-of-data-

СВЯЗНЫЕ СПИСКИ


class Node {
	protected:
		Node *_next;
		Node *_prev;
	public:
		Node (void);
		virtual -Node (void);
		Node *next(void);
		Node *prev(void);
		Node *insert(Node*);
		Node *remove(void)'
		void splice(Node*);
};


Node::-Node(void)
{
}

Node *Node::next(void)
{
	return _next;
}

Node *Node::prev(void)
{
	return _prev;
}


Включение узла в связный список

Node *Node::insert(Node *b)
{
	Node *c = _next;
	b->next = c;
	b -> _prev = this;
	_next = b;
	c -> _prev = b;
	return b;
}

Удаление узла из списка

Node *Node::remove(void)
{
	_prev->_next = _next;
	_next->prev=_prev;
	_next = _prev = this;
	return this;
}


Соединение/разъединение 2 узлов 
void Node::splice (Noda *b)
{
	Node *a = this;
	Node *an = a -> _next;
	Node *bn = b -> _next;
	a ->_next = bn;
	b ->_next = an;
	an->_prev = b;
	bn ->_prev = a;
}





СПИСКИ


template<class T> class ListNode : public Node {
	public:
		ListNode(T val);
		friend class List<T>;
};



template<class T> ListNode::ListNode(T val) :
	_val(val)
{
}


template<class T> class List{
	private:
		ListNode<T> *header;
		ListNode<T> *win;
		int _lenght;
	public:
		List (void);
		-List(void);
		T insert(T);
		T append(T);
		List *append(List *);
		T prepend(T);
		T remove(void);
		void val(T);
		T val (void);
		T next (void);
		T prev (void);
		T first (void);
		T last (void);
		int length (void);
		bool isFirst (void);
		bool isLast(void);
		bool isHead (void);
};



Конструктор/Диструктор

template<class T> List<T>::List(void) :
	_length(0)
{
	header = new ListNode<T> (Null);
	win = header;
}



template<class T> List<T>::~List(void)
{
	while (length{} > 0{
		first{};
		remove {};
		}
	delete header;
}


Изменение списков 


template<class T> T List<T>::insert(T val)
{
	win ->insert(new ListNode<T>(val));
	++_length;
	return val;
	
}



template<class T> T List<T>::prepend(T val)
{
	header ->insert(new ListNode<T>(val));
	++_length;
	return val;
}


template<class T> T List<T>::append(T val)
{
	header ->prev() -> insert (new ListNode<T>(val));
	++_length;
	return val;
}


template<class T> List<T>* List<T>::append(List<T> *l)
{
	ListNode<T> *a = ListNode<T>*) header -> prev();
	a -> splice (l->header);
	_length += ; -> _length;
	l ->header->remove();
	l->_length = 0;
	l->win = header;
	return this;
}


template<class T> T List<T>::remove(void)
{
	if (win == header)
		return NULL;
	void *val = win ->_val;
	win = (ListNode<T>*)win->prev();
	delete (listNode<T>*)win->next()->remove();
	--_length;
	return val;

}


void List<T>::val (T v)
{
	if (win != header)
		win -> _val = v;
}


Доступ к элементам списка 

template<class T> T List<T>::val(void)
{
	return win->_val;
}


template<class T> T List<T>::next(void)
{
	win = (ListNode<T>*) win->prev();
	return win->_val;
}


template<class T> T List<T>::first(void)
{
	win = (ListNode<T>*) header->next();
	return win->_val;
}



templlate<class T> T List<T>::last(void)
{
	win = (ListNode<T>*) header->prev();
	return win->_val;
}



template<class T> int List<T>::length(void)
{
	return _length;
}



template<class T> bool List<T>::isFirst(void)
{
	return ((win ==header ->next()) && (_legth > 0));
}


template<class T> bool List<T>::isLast(void)
{
	return ((win ==header ->()) prev&& (_legth > 0));
}


template<class T> bool List<T>::isHead(void)
{
	return (win == header);
}


Примеры списков 


template<class T> List<T> *arrayToList(T a[], int n)
{
	List<T> *s = new List<T>;
	for (int i = 0; i < n; i++)
		s ->append(a[i]);
	return s;
}



template<class T> T leastItem(List<T> *s, int(*cmp) (T,T))
{
	int i;
	if (s.length() == 0)
		return NULL;
	T v = s.first();
	for (s.next(); !s.isHead(); s.next())
		if (cmp(s.val(), v) < 0)
			v = s.val();
	return v;

}


List<char*> s;
s.append("bat");
s.append("ant");
s.append("cat");

cout << leastItem(s, strcmp);



СТЭК



template<class T> class Stack {
private:
	List<T> *s;
public:
	Stack(void);
	~Stack(void);
	void push(T v);
	T pop(void);
	bool empty(void);
	int size(void);
	T top(void);
	T nextToTop(void);
	T bottom(void);
};




template<class T> Stack<T>::~Stack(void):
{
	delete s;
}


template<class T> void Stack<T>::push(T v):
{
	s->prepend(v);
}

template<class T> T Stack<T>::pop(void):
{
	s -> first();
	return s -> remove();
}


template<class T> bool Stack<T>::empty(void)
{
	return (s -> length() == 0);
}


template<class T> int Stack<T>::size(void)
{
	return s -> length();
}


template<class T> T Stack::top(void)
{
	return s->first();
}


template<class T> T Stack::nextToTop(void)
{
	s ->first();
	return s->next();
}


template<class T> T Stack::bottom(void)
{
	return s->last();
}

void reverse(char *s[], int n)
{
	stack<char*> s;
	for (int i = 0; i < n; i++)
		s.push(a[i]);
	for (i = 0; i<n; i++)
		a[i] = s.pop();
}



Двоичные деревья 


template<class T> class TreeNode{
	protected:
		TreeNode *_ichild;
		TreeNode *_rchild;
		T val;
	public:
	TreeNode(T);
	virtual ~TreeNode(void);
	friend class SearchTree<T>;
	friend class BraideSearchTree<T>;
};





template<class T> TreeNode<T>::TreeNode(T v) :
	val(v), _lchild(NULL), _rchild(NULL)
{
}


template<class T> TreeNode<T>::~TreeNode(void)
{
	if (_lchild) delete _lchild;
	if (_rchild) delete _rchild;
}





ДЕРЕВО ПОИСКА

template<class T> class SearchTree {
	private:
		TreeNode *root;
		int (*) (T, T) cmp;
		TreeNode<T> * findMin(TreeNode<T> *);
		void _remove(T, TreeNode<T> * s);
		void _inorder(TreeNode<T> *, void (*) (T));
	public:
		SearchTree (int(*) (T, T) );
		~SearchTree (void);
		int isEmpty(void);
		T find(T);
		T findMin(void);
		void inornder(void(*) (T));
		void remove(T);
		T removeMin(void);
};



3.5.4 конструкторы и деструкторы 













































































































































































































































































































































































































































































































































































































































































































































































