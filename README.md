# Null safety
ما هو Sound null Safety ؟
هو لتاكد ان قيمة المتغيرات او الثوابت عند تعريفها ليست خالية ومتاكدين بنسبة 100% من القيمة. ما لم تتم تهيئته مع قيمة لهذا المتغير. او تهيئته ليستقبل قيمه خالية 
 مع مفهوم null safety، سيتم عرض جميع الاخطاء في وقت التشغيل (runTime) .
 
 لماذا  **null safety ؟**
 
 تعتبر Dart لغة من النوع الآمن. هذا يستنتج أنه عندما تحصل على متغير أو ما شابه ، يمكن للمترجم أن يضمن أنه من هذا النوع ويحتوي قيمه ما لم يتم تعريفه لكي يستقبل قيمه فارغه 
 
 
 مفهوم  **Non-nullable:**
 وهو مفهوم ان القيمه لا تقبل قيمة null او قيمة خالية 

 مثال :

    void main(){
    String name = "Ahmed Seed" ;
    print(name);
    }

 وهو تعريف المتغير وعطائه قيمة عند تعريفه  كما هو الحال في المثال في الاعلى 
 المخرجات :
 

    Ahmed Seed

في المخرجات نلاحظ تم طباعة الاسم لاكن ماذا لو كانت القيمه خاليه او تم اعطائها null مالذي سوف يحدث ؟

في المثال بالاسفل سوف نرا مالذي سوف يحدث في حال لم يتم اعطاء المتغير قيمه عند تعريفها 
 مثال :

    void main(){
    String name ;
    print(name);
    }

 وهو تعريف المتغير وعطائه قيمة عند تعريفه  كما هو الحال في المثال في الاعلى 
 المخرجات :
 

     Non-nullable variable 'name' must be assigned before it can be used.
    print(name);
          ^^^^

 
 تم الاشاره الى الى ان هذا المتغير هو عباره عن Non-nullable يجب اعطائه قيمه في وقت تعريف المتغير ولا يمكن التعامل معه بدون قيم  
 
  مفهوم **nullable:**
  وهو  ان القيمه  تقبل قيمة null او قيمة خالية ويمكن تعريف متغير وسناد القيمه له في وقت أخر
  

    void main(){
    String? name ;
    print(name);
    }

 
 المخرجات :
 

    null

سوف نلاحظ طباعة null لان المتغير من نوع nullable يقبل قيمة null .
يتم استخدام مبدئ nullable في حال لم يتم التاكد من القيمه او تريد اسناد القيمه في وقت لاحق او قد تكون القيمه خاليه ويمكن تحويل المتغير من نوع Non-nullable الى nullable فقط بستخدام علامة (؟)







**مفهوم null safety مع List** 

لو اردنا انشاء List بدون عمل لها تهيئه (initialize) ثم حاولنا طباعة هذه list سوف يتم اظهار خطاء لان list هي عباره عن non-nullable يجب عمل لها تهيئه.
لناخذ مثال لتوضيح المفهوم 

مثال :




    void main() {
    List studentsName;
    print(studentsName);
    }

سوف تظهر لنا رساله 

     Non-nullable variable 'studentsName' must be assigned before it can be used.
    print(studentsName);

في المثال في الاعلى ظهر لنا خطاء يشير ان المتغير هو Non-nullable variable ولحل هذه المشكله يتم في طريقتين  اما باسناد له list خاليه بستخدام =[] او بستخدام مفهوم nullable كما في الاسفل 


    void main() {
    List? studentsName;
    print(studentsName);
    }

المخرج 

    null

نلاحظ تم حل المشكله بستخدام علامة ؟ عند اضافتها على نوع المتغير  list  بهذه الطريقه يمكن ان تقبل List قيمة null 


**استخدام مفهوم null safety مع العناصر داخل list** 
لو ادرنا انشاء list من نوع String وضفنا قيم لها هي عباره عن اسماء الطلاب واحد هذه القيم هي عباره عن null سوف تظهر لنا رسالة خطاء لان المتغير من نوع list لا يقبل الى نصوص 

مثال 


    void main() {
    List<String>? studentsName = ["Ahmed","Ali","Reem",null,"Sara"];
    print(studentsName);
    }

المخرجات:

    The value 'null' can't be assigned to a variable of type 'String' because 'String' is not nullable.
    List<String>? studentsName = ["Ahmed","Ali","Reem",null,"Sara"

نلاحظ في المثال في الاعلى ظهرة لنا رساله توضح لنا مشكلة الخطاء وحل هذه المشكله يتم اضافة علامة الاستفهام داخل الاقواس   <> الخاصه في list عند نوع المتغير  String كما هو موضح في الاسفل 


    void main() {
    List<String?>? studentsName = ["Ahmed","Ali","Reem",null,"Sara"];
    print(studentsName);
    }

المخرجات :

    [Ahmed, Ali, Reem, null, Sara]

بهذا الشكل اصبحت هذه list تقبل قيم عباره عن null 

ويمكن تطبيق المفهوم على maps ايضا في حال اردت تعريف map 

 
 
 
 
 
 مسودة
