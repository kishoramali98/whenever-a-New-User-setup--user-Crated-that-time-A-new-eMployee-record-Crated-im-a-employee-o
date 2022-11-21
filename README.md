# whenever-a-New-User-setup--user-Crated-that-time-A-new-eMployee-record-Crated-im-a-employee-o
whenever a New User(setup -user) Crated that time A new eMployee record  Crated      im a employee object 
trigger userCreated on User (After insert)
{  
    
  Map<id,user> myuser = trigger.NewMap;
    set<id>usedId = myuser.keySet();
    classofEmployeee.userToEmp(usedId);
}



public class classofEmployeee 
{

   @feature
  public static void userToEmp(set<id> useId)
  {
      List<User> newUserList = [select id,Name,LastName,Email,Phone From user Where id IN :useId];
list<Employee__c > elist=new list<Employee__c >();
      for(User eachuser:newUserList)
      {
         Employee__c Emp=New Employee__c();
          Emp.Employee_Name__c=eachUser.Name;
          Emp.Employee_LastName__c=eachUser.LastName;
          Emp.Employee_Phone__c=eachUser.Phone;
          Emp.Employee_Email__c=eachUser.Email;
          Emp.Name=eachUser.Name +''+eachUser.LastName;
           elist.add(Emp);
     }
          
          
      
  }
}
