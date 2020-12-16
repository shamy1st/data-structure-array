# Array

![](https://github.com/shamy1st/data-structure/blob/main/images/array.png)

--                 | indexing | search | add    | remove(index or value)
-------------------|----------|--------|--------|-----------------------
Basic Array        | O(1)     | O(n)   | -      | -
Dynamic Array      | O(1)     | O(n)   | O(n)   | O(n)
    
        public class Main {
            public static void main(String[] args) {
                Array array = new Array(3);
                array.insert(10);
                array.insert(20);
                array.insert(30);
                array.insert(40);
                System.out.println(array.indexOf(40));
                array.removeAt(1);
                array.print();
            }
        }

        public class Array<T> {
            private T[] items;
            private int count;

            public Array(int length) {
                items = (T[]) new Object[length];
            }

            //O(n)
            public void insert(T item) {
                if(items.length == count) {
                    T[] temp = (T[]) new Object[items.length * 2];
                    for(int i=0;i<items.length;i++)
                        temp[i] = items[i];

                    items = temp;
                }
                items[count++] = item;
            }

            //O(n)
            public void removeAt(int index) {
                if(index < 0 || index >=count)
                    throw new ArrayIndexOutOfBoundsException();

                for(int i=index;i<count;i++)
                    items[i] = items[i+1];

                count--;
            }

            //O(n)
            public int indexOf(T item) {
                for(int i=0;i<count;i++)
                    if(items[i].equals(item))
                        return i;
                return -1;
            }

            public void print() {
                for(int i=0;i<count;i++)
                    System.out.println(items[i]);
            }
        }
