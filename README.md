# iterators
class Fibonacci:
    def __init__(self, stop):
        self._current = 0
        self._stop = stop
        self._index = 0
        self._next = 1

    def __iter__(self):
        return self

    def __next__(self):
        if self._index < self._stop:
            self._index += 1
            fibo_number = self._current
            self._current, self._next = self._next, self._current + self._next

            return fibo_number
        else:
            raise StopIteration


fibo_iterator = Fibonacci(5)
for i in fibo_iterator:
    print(i)


# # 0 1 1 2 3 5 8 13 ..

import psycopg2


database = 'telephone',
user = 'postgres',
password = 'Bukhara04',
port = 5433,
host = 'localhost'

conn = psycopg2.connect(host = host,
                        database = database,
                        user = user,
                        port = port,
                        password = password
                        )

cur = conn.cursor()
create_telephone_table = """
                    create table telephone(
                    id serial primary key,
                    name varchar(10),
                    price int);
                    )
"""

cur.execute(create_telephone_table)
conn.commit()

insert_telephone = """
            insert into
        telephone(name,price)

        values('XII',300);
"""

cur.execute(insert_telephone)
conn.commit()

select_table = """
                select * from telephone;
"""

cur.execute(select_table)
conn.commit()
cur.execute(select_table)
for i in cur.fetchall():
      print(i)
