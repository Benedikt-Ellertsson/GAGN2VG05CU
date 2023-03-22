# GAGN2VG05CU
##Verkefni 1 - kóði  
###2: Birta upplýsingar um einn ákveðinn áfanga með Stored Procedure  

delimiter €€  
drop procedure if exists Afangi €€  

create procedure Afangi(afangi_id CHAR(15))  
begin  
	select * from Courses where courseNumber = afangi_id;  
end €€  

delimiter ;  

call afangi('ENSK2OF05BT');  



###3: Nýskráning áfanga með Store Procedure  

delimiter €€  
drop procedure if exists Nyr_Afangi €€  
create procedure Nyr_Afangi(afanga_nr char(15),nafn_afanga varchar(75),einingar tinyint)  
begin  
	insert into Courses(courseNumber,courseName,courseCredits)  
    values(afanga_nr,nafn_afanga,einingar);  
    select row_count();  
end €€  
delimiter ;  
call Nyr_Afangi('TEST230BF','Test','5');  



###4: Uppfæra áfanga með Store Procedure  

delimiter €€  
drop procedure if exists UppfaeraAfanga €€  
create procedure UppfaeraAfanga(course_number char(15), new_course_number char(15), new_course_name varchar(75), new_course_credits tinyint)  
begin  
	update Courses  
	set courseNumber = new_course_number, courseName = new_course_name, courseCredits = _new_course_credits  
	where courseNumber = course_number  
end €€  
delimiter ;  
call UppfaeraAfanga('TEST230BF','TEST990DF','Test uppfært','3');  



###5: Eyða áfanga úr grunninum með Store Procedure  

delimiter €€  
drop procedure if exists EydaAfanga €€  
create procedure EydaAfanga(course_number char(15))  
begin  
	if not exists(select * from TrackCourses where courseNumber = course_number) then  
		delete from Courses  
		where courseNumber = course_number;  
	end if;  
end €€  
delimiter ;  
call EydaAfanga('Test990DF');  



###6: Reikna út(telja) heildarfjölda áfanga með Function  

delimiter €€  
drop function if exists TeljaAfanga €€  
CREATE FUNCTION TeljaAfanga()  
returns int  
deterministic  
begin  
	RETURN (SELECT COUNT(*) FROM Courses);  
end €€  
delimiter ;  



###7: Function sem telur einingar sem eru í boði á ákveðinni námsleið(Track)  
delimiter €€  
drop function if exists TrackCredits €€  
CREATE FUNCTION TrackCredits(track_ID)  
return int deterministic  
begin  
	declare creditSum int;  

	Select sum(Courses.courseCredit) into creditSum  
	from Courses  
	inner TrackCourses on Courses.courseNumber = TrackCourses.courseNumber and trackCourses.trackID = track_id;  

	return creditSum;  
end €€  
delimiter ;  
###8: Skrifa Function sem kannar hvort ákv. dagsetning(date) sé á hlaupári  


###9: Skrifa Function sem reiknar út aldur ef upp er gefin dagsetning(date)  
###10: Stored Procedure sem skila öllum nemendum á ákveðinni önn(semester)  

delimiter €€  
drop procedure if exists NemendurAnnar €€  
create procedure NemendurAnnar(semester_id int)  
begin  
