```sql
INSERT INTO user (username, email, password, height, age, has_subscription) VALUES 
('minjung','abc@gmail.com',25, 165, 25, 0),
('지민','def@gmail.com',26, 170, 25, 0);



CREATE TABLE user (
  user_id INTEGER PRIMARY KEY AUTOINCREMENT,
  username TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL, -- DB에 해당 이메일이 있는지 확인한다.
  password TEXT NOT NULL,
  address TEXT,
  age INTEGER CHECK (age BETWEEN 0 AND 100), -- 음수값과 나이제한을 걸어둔다.
  height REAL CHECK (height BETWEEN 10.0 AND 250), -- 음수 값과 최대 키값을 체크해야 한다.
  has_subscription INTEGER NOT NULL DEFAULT 0 CHECK (has_subscription BETWEEN 0 AND 1) -- 기본 값을 0 (false)로 설정한다.
);

DROP TABLE user;

-- Data Manipulation LANGUAGE
-- Update Commands : 데이터를 수정 / 편집 / 삭제
-- Query Commands : select

-- 1. Update Commands
-- INSERT INTO VALUES 
INSERT INTO user 
	(username, email, password, height, age, has_subscription) 
VALUES 
	('민정','abc@gmail.com',25, 165, 25, 0),
	('지민','def@gmail.com',26, 170, 25, 0),
	('해원','123@gmail.com',23, 162, 23, 0),
	('안유진','456@gmail.com',23, 170, 23, 0);

-- UPDATE
-- 모든 구독 정보를 업데이트 시킨다.
UPDATE user SET has_subscription = 1;
-- 한 유저의 구독 정보를 업데이트 시킨다.
UPDATE user SET has_subscription = 0 WHERE username = "해원";
-- 행 값을 참조하여 업데이트
UPDATE user SET height = height + 20 WHERE username = "안유진";
-- 특정 조건 업데이트
UPDATE user SET address = "KOREA" WHERE address is NULL;

-- DELETE
-- 유저 정보 모두 삭제
DELETE FROM user;
-- 한 유저 정보 삭제
DELETE FROM user WHERE user_id = 3;

-- SELECT 받을 열의 값, ...
-- table의 결과물을 제공하는 명령어
SELECT 1+1, 2+2, "hello";
-- 모든 유저정보 가져오기
SELECT * FROM user;
-- 모든 유저 이름 가져오기
SELECT username FROM user;
-- 모든 유저이름 / 이메일 가져오기
SELECT username, email FROM user;
-- 가져올 열의 이름을 바꾸기
SELECT 
	username as user_name, 
	email 
FROM 
	user;
-- 값을 수정해서 가져오기
SELECT 
	username as user_name, 
	REPLACE(email, ".com", ".co.kr") AS e_mail
FROM 
	user;

```