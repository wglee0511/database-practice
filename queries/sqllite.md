```sql
INSERT INTO user (username, email, password, height, age, has_subscription) VALUES 
('minjung','abc@gmail.com',25, 165, 25, 0),
('지민','def@gmail.com',26, 170, 25, 0);



CREATE TABLE user (
  user_id INTEGER PRIMARY KEY AUTOINCREMENT, -- AUTOINCREMENT 사용시 항상 고유한 값을 갖을 수 있다.
  username TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL, -- DB에 해당 이메일이 있는지 확인한다.
  password TEXT NOT NULL,
  address TEXT,
  age INTEGER CHECK (age BETWEEN 0 AND 100), -- 음수값과 나이제한을 걸어둔다.
  height REAL CHECK (height BETWEEN 10.0 AND 250), -- 음수 값과 최대 키값을 체크해야 한다.
  has_subscription INTEGER NOT NULL DEFAULT 0 CHECK (has_subscription BETWEEN 0 AND 1) -- 기본 값을 0 (false)로 설정한다.
);

DROP TABLE user;



```