出處[Unit Test Framework – JUnit 4](https://kkboxsqa.wordpress.com/2014/06/30/unit-test-framework-junit-4/)
這篇文章對於使用JUnit4寫得非常清楚。因此進行筆記與截錄。

# 要如何寫
1. Import JUnit 4 Library
2. 寫一個 JUnit 4 Test 的 Class
3. 執行 JUnit 4 測試

## 2. 寫一個 JUnit Test 的 Class
假設今天要利用 JUnit 4 測試一個 method，必須掌握以下幾個要點：
1. 在 test method 上面加上 @test
2. @Before：會在每一個 @test 前先執行一次，就像 JUnit 3 的 setUp.
3. @After：會在每一個 @test 後再執行一次，就像 JUnit 3 的 tearDown.
4. @BeforeClass：會在執行 class 前會先執行一次
5. @AfterClass：會在執行完 class 後會再執行一次
6. assertEquals：幫助檢驗執行結果與預期結果是否相等 //真正的執斷言的方法參數為(預期值, 實際值)

通常在assertEquals的上方會寫實例化，以便使用類別內的方法與屬性。

```java
//做為範例的程式碼
public class JUnit4TestCalculator {
    @BeforeClass
    public static void beforeClass()
    {
        System.out.println("@BeforeClass");
    /* 開始 Test Class 前的準備工作：開啟計算機... */
 
    }
 
    @Before
    public void before()
    {
        System.out.println("@Before");
    /* 開始 Test Case 前的準備工作：將計算機歸零... */
 
    }
 
    @AfterClass
    public static void afterClass()
    {
        System.out.println("@AfterClass");
    /* 完成 Test Class 後的恢復工作：關閉計算機... */
 
    }
 
    @After
    public void after()
    {
        System.out.println("@After");
    /* 完成 Test Case 後的恢復工作：將計算機歸零... */
 
    }
 
    @Test
    public void testSubtraction()
    {
    Calculator calculator = new Calculator();
        System.out.println("@Test - testSubtraction()");
        Assert.assertEquals(0, calculator.subtraction(0, 0));
    }
 
    @Test
    public void testAdd()
    {
        Calculator calculator = new Calculator();
        System.out.println("@Test - testAdd()");
        Assert.assertEquals(0, calculator.add(0, 0));
    }
}
```

實際執行順序會是：
+ @BeforeClass
+ @Before
+ @Test – testSubtraction()
+ @After
+ @Before
+ @Test – testAdd()
+ @After
+ @AfterClass

有這樣的基本架構這樣就可以執行 JUnit 4 了。
按滑鼠右鍵Run。
