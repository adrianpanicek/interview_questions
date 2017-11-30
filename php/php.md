# Backend PHP developer interview questions

### Syntax and functionality

1. What will be the output of following statement?
    ```php
    echo (int) ((0.1 + 0.7) * 10);
    ```
    - A: 7
    - B: 6
    - C: 8
    - D: 0
    
1.  Please fix the next PHP code. It should change the content of two variables without using return.
    ```php
    function swap($a, $b)
    {
        $c = $a;
        $a = $b;
        $b = $c;
    }
    
    $x = 10;
    $y = 20;
    echo $y / $x; // 2
    swap($x, $y);
    echo $y / $x; // 0.5
    ```

1. Which condition in following statement will match and why?
    ```php
    $a = '0';
    if ($a == 0) { ... }
    if ($a === 0) { ... }
    ```
    
1. Write down the result of following statement
    ```php
    echo json_encode([
        'id' => 123,
        'method' => 'test',
        'params' => [
            'accounts' => [15, '14'],
            'date' => '2014-03-24'
        ]
    ]);
    ```
    
1. How to fix following code
    ```php
    $conn = $db->connect($config); // Fatal error: Uncaught RuntimeException: Connection interrupted
    if (!$conn) {
        echo "Connection was not sucessful";
    }
    echo "Connection was successful";
    ```
    
1. What is wrong with following code?
    ```php
    class Vehicle
    {
        protected $tiresSize = 22;
        
        private function getTiresSize()
        {
            return self::$tiresSize;
        }
        
        private static function getName()
        {
            return "Truck";
        }
        
        public function getParams()
        {
            return $this->getName() . ": " . self::getTiresSize();
        }
    }
    
    $car = new Vehicle();
    echo $car->getParams();
    ```

1. What will be output of following code ?
    ```php
    function test($int) 
    {
        try {
            $int++; 
            try {
                throw new Exception("ex");
                $int -= 1; 
            } catch (Exception $e) {
                $int++; 
            } finally {
                $int--; 
                throw new Exception("ex");
            }
        } catch (Exception $e) {
            $int += 1;   
        } finally {
            return $int--; 
        }
        return $int;
    }
    echo test(1);
    ```

1. Explain what is an **anonymous function**. Provide example.

1. Explain what are:
    - Namespaces
    - Traits

1. What is the meaning of a **final class** or **final method**?

1. Can you explain what **XSS** and **CORF** is ?

### Software composition and OOP

1. Explain difference between **class** and **interface**

1. Does the PHP support **direct multiple inheritance**?

1. What are three visibility keywords of **property** or **method**?

1. Explain shortly what Lazy Loading is.

1. What are ways to load classes in PHP?

1. What is **Dependency Injection**? Why are we using it?

1. Explain what **MVC** means.

1. Do you know how to write **unit tests**?

### Databases

1. When are you using **COMMIT** and **ROLLBACK** commands in SQL database?

1. What is ORM ? What ORM's you have experience with ?

1. Create query to get **result** from **Table A**

    **Table A**
    | id 	| account 	| amount 	|
    |----	|---------	|--------	|
    |  1 	|    5015 	|    100 	|
    |  2 	|    5015 	|    200 	|
    |  3 	|    1004 	|      5 	|
    |  4 	|    1004 	|     15 	|
    |  5 	|    1005 	|     20 	|
    |  6 	|    1005 	|     20 	|
    |  7 	|    2015 	|     14 	|
    |  8 	|    1000 	|     10 	|
    |  9 	|    2100 	|     10 	|
    | 10 	|    2100 	|     10 	|
    
    **Result**
    | account 	| balance 	|
    |---------	|---------	|
    |    5015 	|     314 	|
    |    1004 	|      20 	|
    |    1005 	|      40 	|
    |    1000 	|      10 	|
    |    2100 	|      20 	|
    
1. What field type would you prefer to use for storing **currency values** in mysql, and why ?
 
1. What are **indexes** in table? How and why would you use them?
 
1. Describe differences between **InnoDB** and **MyISAM**.

1. What happens when the SQL table column type is set to INT AUTO INCREMENT, and you reach the maximum value for that table? What can be the solution?

1. Can you tell the difference between **LEFT**, **RIGHT** and  **INNER JOIN**?

1. Can you tell the difference between **UNION** and **UNION ALL**?

1. What will be the result of the query below?
    ```sql
    SELECT
    	SWITCH t.data
    		WHEN 1 THEN 'spooky'
    		WHEN 2 THEN 'spider'
    	ELSE
    		t.data
    	END AS SpookyText
    FROM
    	`transaction` t;
    ```
    
1. What is wrong with this SQL query ?
    ```sql
    SELECT 
    	id, YEAR(BillingDate) AS BillingYear 
    FROM 
    	Invoices
    WHERE 
    	BillingYear >= 2010;
    ```
    
1. What is the execution plan? How would you view the execution plan?

1. What is the difference between **TRUNCATE** and **DELETE**?

1. Describe, what **"OPTIMIZE TABLE"** command is doing

1. What is the difference between **TRUNCATE** and **DELETE**?

1. Can you explain what **SQL injection** is.

### Tooling and development processes

1.	Using CURL; which command is missing from the next code?
    ```php
    $defaults = array(
            CURLOPT_POST => 1,
            CURLOPT_URL => $url,
            CURLOPT_RETURNTRANSFER => TRUE,
            CURLOPT_TIMEOUT => 30,
            CURLOPT_SSL_VERIFYHOST => false,
            CURLOPT_SSL_VERIFYPEER => false,
            CURLOPT_POSTFIELDS => json_encode($request),
            CURLOPT_VERBOSE=>TRUE
       );
       $ch = curl_init();
       curl_setopt_array($ch, $defaults);
       $result = _______________________($ch);
    ```
    
    - **A**: curl_execute
    - **B**: curl_exec
    - **C**: curl_run

1. Which command is used in GIT for branch merging?

1. What is difference between **composer install** and **composer update**, what purpose **composer.lock** serve?

1. Describe following command graphically:  **git reset --hard HEAD~1**

1. Can you describe what **scrum** means? Have you ever worked in scrum?

### Standards and Best practices

1. Do you know what PSR standards are? Can you name some?

1. Do you know what **linting** and **static code analysis are** ?

1. Do you know what **DRY** and **KISS** are?

1. Name formatting changes you would do if you saw code like this.

    ```php
    class connectionException extends Exception{
        private $c = null;
        
        public function __construct($message, $code = 0, Exception $previous = null, Connection $c){
            parent::__construct($message, $code, $previous);
             $this->c = $c;
        }
        
        function get_connection() {
         return $c;
        }
    
    
    }
    ```

### Language specific problems

1. Look at this code, what will be output and why?
    ```php
    $a = [];
    $a[1] = 'c';
    $a[2] = 'b';
    $a[0] = 'a';
    
    echo end($a);
    ```

1. Look at this code, what will be output on PHP 5.6 32bit and why ?
    ```php
    for ($i = 2017; $i < 2050; $i++) {
    	echo date('d.m.Y’, strtotime($i . ‘-01-01’));
    }
    ```
    
1. Which of the following statements will be true? Why?

    ```php
    0154 == 154;
    "0154" == 154;
    '0154' == 154;
    'tab\ttest' == "tab\ttest";
    ```

### Opinionated questions

1. What type of **editor/IDE** do you use and why?

1. Are you developing any **personal project**?

1. Would you do (or are you doing) **open-source**?


