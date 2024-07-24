social media platform

 create table Users(
  2  User_id int primary key,
  3  Username varchar(20),
  4  Email_id varchar(100),
  5  Password varchar2 (10),
  6  Full_name varchar2 (30),
  7  Birth_date date);

Table created.
 DESC USERS;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 USER_ID                                   NOT NULL NUMBER(38)
 USERNAME                                           VARCHAR2(20)
 EMAIL_ID                                           VARCHAR2(100)
 PASSWORD                                           VARCHAR2(10)
 FULL_NAME                                          VARCHAR2(30)
 BIRTH_DATE                                         DATE

 insert into users values(24,'arpita24','arp@gmail.com',12345,'arpita jain','24-jun-2003');

1 row created.
 
insert into users values(12,'mohit05','moh@gmail.com',54321,'mohit jain','05-jul-2000');

1 row created.

insert into users values(15,'sanjay07','san@gmail.com',09876,'sanjay jain','18-aug-1974');

1 row created.

insert into users values(09,'asmita15','asm@gmail.com',67890,'asmita jain','15-oct-1981');

1 row created.

select*from users;

   USER_ID USERNAME          EMAIL_ID                                                                    PASSWORD   FULL_NAME         BIRTH_DAT
---------- -------------------- ---------------------------------------------------------------------------------------------------- ---------- ------------------------------ ---------
        24 arpita24             arp@gmail.com                                                                                        12345      arpita jain       24-JUN-03
        11 mohit05              moh@gmail.com                                                                                        54321      mohit jain        05-JUL-00
        12 mohit05              moh@gmail.com                                                                                        54321      mohit jain        05-JUL-00
        15 sanjay07             san@gmail.com                                                                                        9876       sanjay jain       18-AUG-74
         9 asmita15             asm@gmail.com                                                                                        67890      asmita jain       15-OCT-81


create table Posts(
  2  Post_id int primary key,
  3  User_id int,
  4  Content varchar(10),
  5  Likes_count int,
  6  Comments varchar2(20),
  7  foreign key (user_id) references users(user_id));

Table created.

desc posts;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 POST_ID                                   NOT NULL NUMBER(38)
 USER_ID                                            NUMBER(38)
 CONTENT                                            VARCHAR2(10)
 LIKES_COUNT                                        NUMBER(38)
 COMMENTS       

insert into posts values(22,24,'ideas',123,'great');

1 row created.

 insert into posts values(55,12,'accounts',3456,'amazing');

1 row created.

 insert into posts values(99,15,'trading',883974,'helpful');

1 row created.

insert into posts values(47,09,'music',63789,'good');

1 row created.

 SELECT*FROM POSTS;

   POST_ID    USER_ID CONTENT    LIKES_COUNT COMMENTS
---------- ---------- ---------- ----------- --------------------
        22         24 ideas              123 great
        55         12 accounts          3456 amazing
        99         15 trading         883974 helpful
        47          9 music            63789 good



create table Comments (
  2  Comment_id int primary key,
  3  User_id int,
  4  Post_id int,
  5  foreign key (user_id) references users(user_id),
  6  foreign key (post_id) references posts(post_id));

Table created.

 desc comments;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 COMMENT_ID                                NOT NULL NUMBER(38)
 USER_ID                                            NUMBER(38)
 POST_ID                                            NUMBER(38)

insert into comments values (84,24,22);

1 row created.

insert into comments values(92,12,55);

1 row created.

insert into comments values(60,15,99);

1 row created.

insert into comments values(38,09,47);

1 row created.

SELECT*FROM COMMENTS;

COMMENT_ID    USER_ID    POST_ID
---------- ---------- ----------
        84         24         22
        92         12         55
        60         15         99
        38          9         47


create table Videos(
  2  Video_id int primary key,
  3  Post_id int,
  4  User_id int,
  5  Size_of Float,
  6  foreign key (user_id) references users(user_id),
  7  foreign key (post_id) references posts(post_id));

Table created.
 desc videos;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 VIDEO_ID                                  NOT NULL NUMBER(38)
 POST_ID                                            NUMBER(38)
 USER_ID                                            NUMBER(38)
 SIZE_OF                                            FLOAT(126)


insert into videos values(40,22,24,27.889);

1 row created.

insert into videos values(74,55,12,44.976);

1 row created.

insert into videos values(82,99,15,2.864);

1 row created.

insert into videos values(59,47,09,5.986);

1 row created.

SELECT*FROM VIDEOS;

  VIDEO_ID    POST_ID    USER_ID    SIZE_OF
---------- ---------- ---------- ----------
        40         22         24     27.889
        74         55         12     44.976
        82         99         15      2.864
        59         47          9      5.986


 create table Login(
  2  Login_id int primary key,
  3  User_id int,
  4  Password varchar(20),
  5  login_time number(3),
  6  foreign key (user_id) references users(user_id));

Table created.

desc login;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 LOGIN_ID                                  NOT NULL NUMBER(38)
 USER_ID                                            NUMBER(38)
 PASSWORD                                           VARCHAR2(20)
 LOGIN_TIME                                         NUMBER(3)


insert into login values(63,24,'arp123',3);

1 row created.

insert into login values(74,12,'moh456',3);

1 row created.

insert into login values(29,15,'san180',3);

1 row created.

insert into login values(89,09,'asm105',3);

1 row created.

SELECT*FROM LOGIN;

  LOGIN_ID    USER_ID PASSWORD             LOGIN_TIME
---------- ---------- -------------------- ----------
        63         24 arp123                        3
        74         12 moh456                        3
        29         15 san180                        3
        89          9 asm105                        3

create table Friendship(
  2  Friendship_id int primary key,
  3  User_id int,
  4  Friend_id int,
  5  Date_of_connection date,
  6  Status varchar(20),
  7  Foreign key(user_id) references users(user_id));

Table created.

SQL> desc friendship;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 FRIENDSHIP_ID                             NOT NULL NUMBER(38)
 USER_ID                                            NUMBER(38)
 FRIEND_ID                                          NUMBER(38)
 DATE_OF_CONNECTION                                 DATE
 STATUS                                             VARCHAR2(20)

insert into friendship values(87,24,2124,'21-feb-2020','accepted');

1 row created.

insert into friendship values(49,12,5643,'31-dec-2010','pending');

1 row created.

insert into friendship values(93,15,9876,'29-jun-2009','declined');

1 row created.

insert into friendship values(10,09,2176,'14-may-2021','blocked');

1 row created.

SELECT*FROM FRIENDSHIP;

FRIENDSHIP_ID    USER_ID  FRIEND_ID DATE_OF_C STATUS
------------- ---------- ---------- --------- --------------------
           87         24       2124 21-FEB-20 accepted
           49         12       5643 31-DEC-10 pending
           93         15       9876 29-JUN-09 declined
           10          9       2176 14-MAY-21 blocked
