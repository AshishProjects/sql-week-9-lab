CREATE DATABASE newTODO


CREATE TABLE  project (
  projectID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  projectName VARCHAR(250) NOT NULL,
  projectDescription TEXT NOT NULL

);


CREATE TABLE  todoItems (
todoID INT AUTO_INCREMENT PRIMARY KEY,
todoItem VARCHAR(250) NOT NULL,
todoDateAdded DATETIME DEFAULT NOW() NOT NULL,
todoStatus BOOLEAN NOT NULL,
todoDueBy DATETIME, 
projectID INT NOT NULL );


ALTER TABLE todoItems ADD INDEX project_index (todoitem);

ALTER TABLE project ADD INDEX PROJECT_INDEX(`projectName`); 

ALTER TABLE todoItems ADD FOREIGN KEY (projectID) REFERENCES project(projectID);

INSERT INTO project (projectId,projectName, ProjectDescription) VALUES ('1', 'Bring Carrots', ' bring carrots or dont come home');
INSERT INTO project (projectId,projectName, ProjectDescription) VALUES ('2', 'One Piece', 'Will Luffy find the one Piece?');
INSERT INTO project (projectId,projectName, ProjectDescription) VALUES ('2', 'Pay bills', 'Pay the bill on time');

INSERT INTO todoItems ( todoItem, todoDateAdded, todoStatus, projectID) VALUES ('CARROTS','2019-03-09','TRUE','1' );
INSERT INTO todoItems ( todoItem, todoDateAdded, todoStatus, projectID) VALUES ('One Piece found','2019-03-14','TRUE','2' );
INSERT INTO todoItems ( todoItem, todoDateAdded, todoStatus, projectID) VALUES ('Phone Bill','2019-03-09','TRUE','3' );


UPDATE project SET projectDescription = "last month phone bill pending " WHERE projectId = '3';

DELETE FROM todoItems WHERE projectID = '3';
