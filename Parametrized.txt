Declare 
	RNn int;
	RNo int:=&rollno;
	n1 varchar(20);
	p1 int;

	cursor c1 (ROll int) is select * from OSTU1 where RNo=ROLLNO;

	cursor c2 is select ROLLNO from NSTU1;

Begin 
	open c1 (RNo);
	open c2;

	fetch c1 into RNo,n1,p1;
	fetch c2 into RNn;

	if(RNn=RNo) then 
		dbms_output.put_line('Not inserted');
	else 
		insert into NSTU1 values(RNo,n1,p1);
	end if;

	close c1;
	close c2;

exception
	WHEN no_data_found THEN
	dbms_output.put_line('No Data Found in table');

end;
/

/* NSTU1 id shoud not be Primary Key*/


