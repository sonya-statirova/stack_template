#include <stdio.h>
#include <stdlib.h>

//=============================

template <typename any_type>
class Stack
{
	private:
		size_t capacity_;
		size_t size_;
		any_type* data_;
	public:
		Stack();
		Stack(size_t capacity);
		~Stack();
		int Push(any_type x);
		any_type Pop();
		any_type Top();
		int Print();
};

//=============================

template <typename any_type>
Stack<any_type>::Stack():
	capacity_ (10),
	size_ (0),
	data_ ((any_type*) calloc(11, sizeof(any_type)))
{}

//-----------------------------

template <typename any_type>
Stack<any_type>::Stack(size_t capacity):
	capacity_ (capacity),
	size_ (0),
	data_ ((any_type*) calloc(capacity + 1, sizeof(any_type)))
{}

//-----------------------------

template <typename any_type>
Stack<any_type>::~Stack()
{
	capacity_ = 0;
	size_ = 0;
	free(data_);
}

/*Stack::~Stack()//for pointers
{
	capacity_ = 0;
	for (size_t i = 0; i < size_; i++)
		free(data_[i]);
	size_ = 0;
	free(data_);
}*/

//-----------------------------

template <typename any_type>
int Stack<any_type>::Push(any_type x)
{
	any_type* change_ptr = NULL;

	if (size_ == capacity_)
	{
		any_type* change_ptr = (any_type*) realloc(data_, (2 * capacity_ + 1) * sizeof(any_type));
		if (change_ptr == NULL)
			return 1;
		else
		{
			data_ = change_ptr;
			capacity_ *= 2;
		}
	}
	data_[size_++] = x;

	return 0;
}

//-----------------------------

template <typename any_type>
any_type Stack<any_type>::Pop()
{

	if (size_ == 0)
		return 0;

	size_--;

	if (capacity_ % 2 == 0 && size_ << 1 == capacity_ && capacity_ >= 20)
	{
		capacity_ /= 2;
		data_ = (any_type*) realloc(data_, (capacity_ + 1) * sizeof(any_type));
	}

	return data_[size_];
}

//-----------------------------

template <typename any_type>
any_type Stack<any_type>::Top()
{
	if (size_ == 0)
		return 0;

	return data_[size_ - 1];
}

//-----------------------------

template <typename any_type>
int Stack<any_type>::Print()
{
	for (size_t i = 0; i < size_; i++)
		printf("|  %c\n", data_[i]);
}
