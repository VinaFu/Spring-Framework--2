# Spring-Framework--2
# Spring 5 Fundamentals

Define of Spring: kinda Inversion of Control Container, refers to Dependency Injection, work without EJB(Enterprise JavaBeans). Transfer some hard-coded pieces in.

    POJO in Java stands for Plain Old Java Object
    WORA = Write Once Run Anywhere
    
Start from lesson 3, build the pom.xml and other services by yourself

# UNIT 3 Architecture and Project Setup

Demos: <conference>

    1. pom.xml = Project Object Model 项目对象模型
    
        包含有关项目的信息和 Maven 用于构建项目的配置configuration详细信息。 
        dependencies + build(建 Maven) 
    
    2. add Model
       
        基本功能(get/set name) Speaker
        rightClick(Java Folder) - build Class " com.pluralsight.model.Speaker" = 大写指的是 Class
        build [getter and setter] to get the firstname + lastname
        see more about getter and setter at: https://www.w3schools.com/java/java_encapsulation.asp 
        (An instance of Encapsulation)
        get = 返回变量名的值。set = 接受一个参数 (newName) 并将其分配给 name 变量。 this关键字用于引用当前对象(get)
       
        
    3. add Reposiroty
    
        数据存储, 读取数据 (names)
        3.1
        Hibernate = ORM框架，Object_Relative DateBase-Mapping.在Java对象与关系数据库之间建立映射，以实现直接存取Java对象！
        还可以与 JPA = Java Persistence API, defines the management of relational data in the Java applications 比较
        Hibernate ORM tool = to save the state of Java object into the database. It is just a specification.
        
        import model.Speaker;
        import java.util.ArrayList;
        import java.util.List;
    
            < ArrayList & List >
                ArrayList class is used to create a dynamic array that contains objects.
                List interface is used to create a list of elements(objects) that are associated with their index numbers.
        
         插入数据(speaker.setFirstName(" lalala ")) = 因为现在数据很少; setFirstName 从 Speaker 来   
                see code block below:
                
                public List<Speaker> findAll(){
                    List<Speaker> speakers = new ArrayList<Speaker>();  // speakers = []; speakers[0] = speaker

                    Speaker speaker = new Speaker();                    // speaker = object u put in

                    speaker.setFirstName("Vina");
                    speaker.setLastName("Fu");

                    speakers.add(speaker);                              // add each value of object(speaker) into List Speakers 

                    return speakers;
                }
          
        3.2
        Add interface
        rightClick (function bracket) --> Refactor --> Extract Interfaces
        Edit interface name & directory
        Select member --> refactor
                    
                public interface SpeakerRepository {
                    List<Speaker> findAll();
                }           // simple and easy
                
    4. add Service
                
        服务功能不明确
        4.1
        see code block below:
                
                package com.pluralsight.service;

                import com.pluralsight.model.Speaker;       // alt + enter = import
                import com.pluralsight.repository.HibernateSpeakerRepositoryImpl;
                import com.pluralsight.repository.SpeakerRepository;

                import java.util.List;
                public class SpeakerServiceIml implements SpeakerService {      

                    private SpeakerRepository repository = new HibernateSpeakerRepositoryImpl();  // import repository & speakerRepository
                    @Override
                    public List<Speaker> findAll(){         // import Speaker
                        return repository.findAll();
                    }
                }
    
        4.2
        Create interface as above
        @Override appears when u build interface
        implements refers to connect to the Interface <SpeakerService>
                               
    5. add Run
       
       运行程序app，查看结果
       Build "Application(class)" under java file. Just print out the answer.(有点像继承extends)
                
                see code blocks below:
                
                import com.pluralsight.service.SpeakerService;
                import com.pluralsight.service.SpeakerServiceIml;

                public class Application {

                    public static void main(String args[]){
                        SpeakerService service = new SpeakerServiceIml();

                        System.out.println(service.findAll().get(0).getFirstName());        //   print out
                    }
                }
    
    6. Configuration 
                
    通常很难test，所以将它们放入annotations 注释或 .xml configuration 中. ~~~~~~~~

# Spring Configuration Using Java



# Spring Scope and Autowiring



# Spring Configuration Using XML



# Advanced Bean Configuration












