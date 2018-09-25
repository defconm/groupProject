# groupProject
CREATE TABLE Employee (
     asuID number(10) PRIMARY KEY,
     name varchar2(24) NOT NULL,
     phone_number number(10),
     address varchar2(50)
     dNum number(10),
     FOREIGN KEY(dNum) references Deptment(dNum)
     )

CREATE TABLE Deptment (
     dNum number(10) PRIMARY KEY,
     oNum number(10) NOT NULL,
     pNum number(10) NOT NULL,
     dName varchar2(24) NOT NULL,
     managerID number(10),
     FOREIGN KEY(managerID) references Employee(asuID)
         on update null
     )
CREATE TABLE WorksOn (
     asuID number(10),
     tID varchar2(10),
     primary key (asuID, tID),
     foreign key (tID) references Task(tID)
          on update cascade,
     foreign key (asuID) references Employee(asuID)
          on update cascase
          )

CREATE TABLE Comments (
     cID varchar2(10) PRIMARY KEY,
     commment_Text varchar2(max),
     timestate DateTime NOT NULL,
     tID varchar2(24) NOT NULL,
     asuID number(10) NOT NULL,
     FOREIGN KEY(asuID) references Employee(asuID)
          on update cascade
     FOREIGN KEY(tID) references Employee(tID)
          on update cascade
          )
CREATE TABLE Task (
     tID varchar2(24) PRIMARY KEY,
     creattionDate DateTime NOT NULL,
     completion_Status varchar2(5) NOT NULL,
     task_Description varchar2(max),
     dNum number(10) NOT NULL,
     FOREIGN KEY(dNum) references Dept(dNum)
     )
