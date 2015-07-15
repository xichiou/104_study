# 設計模組

* [電子書 - XOOPS模組開發](http://campus-xoops.tn.edu.tw/modules/tad_book3/index.php?op=list_docs&tbsn=4) 
* [Tad 教材網電子書](http://www.tad0616.net/modules/tad_book3/)
 
![](images/XOOPS_structure2.png)

### 參考資料
* [Sublime Text 3 新手上路：必要的安裝、設定與基本使用教學](http://blog.miniasp.com/post/2014/01/07/Useful-tool-Sublime-Text-3-Quick-Start.aspx)
* [參考一](https://sites.google.com/site/xoopsmozuzhizuo/)
* [模組產生器](http://www.myeasy.tw/modules/tad_xmod_maker/index.php?op=mkmod&modsn=42)
* [XOOPS表單範例](http://163.16.182.100/modules/XoopsForm/)
 
### 程式碼
拷貝以下程式碼的方法：用滑鼠在程式碼開頭的地方點一下，在程式碼結束的地方用鍵盤 Shift 加上滑鼠點一下。

### xoops_version.php   

```php
<?php
$modversion = array();

//---模組基本資訊---//
$modversion['name'] = "校園佈告欄";
$modversion['version'] = 1.00;
$modversion['description'] = "校園佈告欄";
$modversion['author'] = "tad";
$modversion['credits'] = "";
$modversion['help'] = 'page=help';
$modversion['license'] = 'GNU GPL 2.0';
$modversion['license_url'] = 'www.gnu.org/licenses/gpl-2.0.html/';
$modversion['image'] = "images/logo.png";
$modversion['dirname'] = basename(dirname(__FILE__));

//---模組狀態資訊---//
$modversion['release_date'] = '2015/07/14';
$modversion['module_website_url'] = 'http://www.yces.chc.edu.tw';
$modversion['module_website_name'] = '永靖國小';
$modversion['module_status'] = 'release';
$modversion['author_website_url'] = '';
$modversion['author_website_name'] = '';
$modversion['min_php']=5.2;
$modversion['min_xoops']='2.5';

//---paypal資訊---//
$modversion ['paypal'] = array();
$modversion ['paypal']['business'] = 'hsienhsi@yces.chc.edu.tw';
$modversion ['paypal']['item_name'] = 'Donation :永靖國小';
$modversion ['paypal']['amount'] = 1;
$modversion ['paypal']['currency_code'] = 'USD';


//---後台使用系統選單---//
$modversion['system_menu'] = 1;


//---模組資料表架構---//
$modversion['sqlfile']['mysql'] = 'sql/mysql.sql';
$modversion['tables'][0] = 'school_news';


//---後台管理介面設定---//
$modversion['hasAdmin'] = 1;
$modversion['adminindex'] = 'admin/index.php';
$modversion['adminmenu'] = 'admin/menu.php';


//---前台主選單設定---//
$modversion['hasMain'] = 1;
//$modversion['sub'][1]['name'] = '';
//$modversion['sub'][1]['url'] = '';


//---模組自動功能---//
//$modversion['onInstall'] = "include/install.php";
//$modversion['onUpdate'] = "include/update.php";
//$modversion['onUninstall'] = "include/onUninstall.php";


//---樣板設定---//
$modversion['templates'] = array();
$i=0;
$modversion['templates'][$i]['file'] = 'school_news_adm_main.html';
$modversion['templates'][$i]['description'] = 'school_news_adm_main.html';

$i++;
$modversion['templates'][$i]['file'] = 'school_news_index.html';
$modversion['templates'][$i]['description'] = 'school_news_index.html';


//---搜尋---//
//$modversion['hasSearch'] = 1;
//$modversion['search']['file'] = "include/search.php";
//$modversion['search']['func'] = "搜尋函數名稱";


//---評論---//
//$modversion['hasComments'] = 1;
//$modversion['comments']['pageName'] = '單一頁面.php';
//$modversion['comments']['itemName'] = '流水號欄位';


//---偏好設定---//
$modversion['config'] = array();
$i=0;
//$modversion['config'][$i]['name']	= '偏好設定名稱（英文）';
//$modversion['config'][$i]['title']	= '偏好設定標題（常數）';
//$modversion['config'][$i]['description']	= '偏好設定說明（常數）';
//$modversion['config'][$i]['formtype']	= '輸入表單類型';
//$modversion['config'][$i]['valuetype']	= '輸入值類型';
//$modversion['config'][$i]['default']	= 預設值;
//$i++;


//---區塊設定---//
//$modversion['blocks'] = array();
$i=1;
//$modversion['blocks'][$i]['file'] = "區塊檔.php";
//$modversion['blocks'][$i]['name'] = 區塊名稱（常數）;
//$modversion['blocks'][$i]['description'] = 區塊說明（常數）;
//$modversion['blocks'][$i]['show_func'] = "執行區塊函數名稱";
//$modversion['blocks'][$i]['template'] = "區塊樣板.html";
//$modversion['blocks'][$i]['edit_func'] = "編輯區塊函數名稱";
//$modversion['blocks'][$i]['options'] = "設定值1|設定值2";
//$i++;

//---通知---//
//$modversion['hasNotification'] = 1;

```
### admin/menu.php   
```php
<?php
$adminmenu = array();
$icon_dir=substr(XOOPS_VERSION,6,3)=='2.6'?"":"images/";

$i = 1;
$adminmenu[$i]['title'] = _MI_TAD_ADMIN_HOME ;
$adminmenu[$i]['link'] = 'admin/index.php' ;
$adminmenu[$i]['desc'] = _MI_TAD_ADMIN_HOME_DESC ;
$adminmenu[$i]['icon'] = 'images/admin/home.png' ;


$i++;
$adminmenu[$i]['title'] = '新聞管理';
$adminmenu[$i]['link'] = "admin/main.php";
$adminmenu[$i]['desc'] = '新聞管理介面' ;
$adminmenu[$i]['icon'] = "images/admin/home.png";


$i++;
$adminmenu[$i]['title'] = _MI_TAD_ADMIN_ABOUT;
$adminmenu[$i]['link'] = 'admin/about.php';
$adminmenu[$i]['desc'] = _MI_TAD_ADMIN_ABOUT_DESC;
$adminmenu[$i]['icon'] = 'images/admin/about.png';
?>

```

### admin/main.php
```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";

//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "動作1":
  admin_do_something();
  break;

  //預設動作
  default:
	show_form();
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/

//當 $op 的值等於「動作1」時，欲執行的函數
function show_form(){
	//利用 global 讓 $xoopsTpl 可以在函數中使用
	global $xoopsTpl;

	$out_content='Hello2!'	;
	//$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
	$xoopsTpl->assign('content' , $out_content);
}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾



?>
```

### templates/school_news_adm_main.html
```html
<!--若要套用bootstrap，請載入以下這三行-->
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/bootstrap/css/bootstrap.css" />
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/bootstrap/css/bootstrap-responsive.css" />
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/css/xoops_adm.css" />

aaaaa

<{$content}>

bbbb

```

### 使用表單 admin/main.php
```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";

//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "動作1":
  admin_do_something();
  break;

  //預設動作
  default:
	show_form();
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/

//當 $op 的值等於「動作1」時，欲執行的函數
function show_form(){
	//利用 global 讓 $xoopsTpl 可以在函數中使用
	global $xoopsTpl;

	//$out_content='Hello2!'	;
	//$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
	//$xoopsTpl->assign('content' , $out_content);
	
	include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");
	
	$form = new XoopsThemeForm("編輯新聞","form", $_SERVER['PHP_SELF']);
	$form->addElement(new XoopsFormLabel("說明", "此為發布新聞的頁面"));
	$main = $form->render();
	
	$xoopsTpl->assign('content' , $main);
	
	
}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾



?>
```
>   

### 使用表單 admin/main.php

```sql

CREATE TABLE `school_news` (
  `sn` smallint(5) unsigned NOT NULL COMMENT '流水號',
  `title` varchar(255) NOT NULL COMMENT '標題',
  `content` text NOT NULL COMMENT '內容',
  `unit` varchar(255) NOT NULL COMMENT '單位',
  `uid` mediumint(8) unsigned NOT NULL COMMENT '發布者',
  `post_date` datetime NOT NULL COMMENT '發布日期'
) ENGINE=MyISAM DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;


ALTER TABLE `school_news`
 ADD PRIMARY KEY (`sn`);


ALTER TABLE `school_news`
MODIFY `sn` smallint(5) unsigned NOT NULL AUTO_INCREMENT COMMENT '流水號';


```


### 新聞新增 main.php
```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";

//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news();
  break;

  //預設動作
  default:
	show_form();
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//儲存新聞
function save_news($sn){
	global $xoopsDB ,$xoopsUser;
	//利用$xoopsUser使用者物件抓取登入者的使用者編號
	$uid=$xoopsUser->uid();

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	if($sn){
		//產生SQL修改語法
		$sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

	}else{
		//產生SQL寫入語法
		$sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
	}

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//儲存成功後轉向並秀出訊息
	redirect_header('main.php', 3, "發布成功！");
}


function show_form(){
	//利用 global 讓 $xoopsTpl 可以在函數中使用
	global $xoopsTpl;

	//$out_content='Hello2!'	;
	//$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
	//$xoopsTpl->assign('content' , $out_content);
	
	include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");
	
	//產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $title) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $content, 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $unit,1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  

  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();
  
	$xoopsTpl->assign('content' , $main);
	
	
}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾
?>

```

### 顯示舊新聞   

```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";
$sn=isset($_REQUEST['sn'])?intval($_REQUEST['sn']):"";


//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news();
  break;

  //預設動作
  default:
	show_form($sn);
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//儲存新聞
function save_news($sn){
	global $xoopsDB ,$xoopsUser;
	//利用$xoopsUser使用者物件抓取登入者的使用者編號
	$uid=$xoopsUser->uid();

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	if($sn){
		//產生SQL修改語法
		$sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

	}else{
		//產生SQL寫入語法
		$sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
	}

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//儲存成功後轉向並秀出訊息
	redirect_header('main.php', 3, "發布成功！");
}


function show_form($sn){
	//利用 global 讓 $xoopsTpl 可以在函數中使用
	global $xoopsTpl,$xoopsDB;
	
	$all=array();
	if($sn){
		//列出指定新聞
		$sql="select * from ".$xoopsDB->prefix("school_news")." where `sn` = '{$sn}'";
	
		//送到資料庫執行
		$result=$xoopsDB->query($sql) or die(mysql_error());
	
	
		//開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
		$all=$xoopsDB->fetchArray($result);
	}

	//$out_content='Hello2!'	;
	//$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
	//$xoopsTpl->assign('content' , $out_content);
	
	include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");
	
	//產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $all['title']) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $all['content'], 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $all['unit'],1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("sn", $sn));
  

  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();
  
	$xoopsTpl->assign('content' , $main);
	
	
}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾



?>
```

### 刪除   
```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";
$sn=isset($_REQUEST['sn'])?intval($_REQUEST['sn']):"";


//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news($sn);
  break;

  case "del":
  	del($sn);
  break;
  
  
  //預設動作
  default:
    show_form($sn);
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//刪除新聞
function del($sn){
	global $xoopsDB;

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	//產生SQL刪除語法
	$sql="delete from `{$table}` where sn='{$sn}'";

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//刪除成功後轉向並秀出訊息
	redirect_header('main.php', 3, "刪除成功！");
}



//儲存新聞
function save_news($sn){
    global $xoopsDB ,$xoopsUser;
    //利用$xoopsUser使用者物件抓取登入者的使用者編號
    $uid=$xoopsUser->uid();

    //將資料表套用前置字串
    $table=$xoopsDB->prefix('school_news');

    if($sn){
        //產生SQL修改語法
        $sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

    }else{
        //產生SQL寫入語法
        $sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
    }

    //將SQL語法送到資料庫，執行失敗會秀出訊息
    $xoopsDB->queryF($sql) or die(mysql_error());

    //儲存成功後轉向並秀出訊息
    redirect_header('main.php', 3, "發布成功！");
}


function show_form($sn){
    //利用 global 讓 $xoopsTpl 可以在函數中使用
    global $xoopsTpl,$xoopsDB;

    $all=array();
    if($sn){
        //列出指定新聞
        $sql="select * from ".$xoopsDB->prefix("school_news")." where `sn` = '{$sn}'";
        
        //送到資料庫執行
        $result=$xoopsDB->query($sql) or die(mysql_error());


        //開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
        $all=$xoopsDB->fetchArray($result);
        
        
    }

    //$out_content='Hello2!'    ;
    //$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
    //$xoopsTpl->assign('content' , $out_content);

    include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");

    //產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $all['title']) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $all['content'], 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $all['unit'],1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("sn", $sn));


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();

    $xoopsTpl->assign('content' , $main);


}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾
'''


### list    
```php

<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";
$sn=isset($_REQUEST['sn'])?intval($_REQUEST['sn']):"";


//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news($sn);
  break;

  case "del":
  	del($sn);
  break;
  
  
  //預設動作
  default:
  	news_list();
    show_form($sn);
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//新聞列表
function news_list(){
	global $xoopsDB ,$xoopsTpl,$xoopsUser;

	//日期從大排到小，列出所有新聞
	$sql="select * from ".$xoopsDB->prefix("school_news")." order by `post_date` desc";


	//送到資料庫執行
	$result=$xoopsDB->query($sql) or die(mysql_error());

	//$all_data 代表所有新聞，預設為空值
	$all_data="";

	//從第0筆資料開始抓取
	$i=0;

	//開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
	while($all=$xoopsDB->fetchArray($result)){

		//抓取其中使用者編號
		$uid=$all['uid'];

		//根據uid轉換成姓名
		$uid_name=$xoopsUser->getVar('name');
		if(empty($uid_name))$uid_name=XoopsUser::getUnameFromId($uid,0);

		//將姓名塞進資料陣列中
		$all['uid_name']=$uid_name;

		//依序的把抓回的資料塞入$all_data中
		$all_data[$i]=$all;

		//資料筆數遞增
		$i++;
	}
	
var_dump($all_data);die();

	//將所有新聞內容送到樣板中
	$xoopsTpl->assign("all_data" , $all_data);



}


//刪除新聞
function del($sn){
	global $xoopsDB;

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	//產生SQL刪除語法
	$sql="delete from `{$table}` where sn='{$sn}'";

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//刪除成功後轉向並秀出訊息
	redirect_header('main.php', 3, "刪除成功！");
}



//儲存新聞
function save_news($sn){
    global $xoopsDB ,$xoopsUser;
    //利用$xoopsUser使用者物件抓取登入者的使用者編號
    $uid=$xoopsUser->uid();

    //將資料表套用前置字串
    $table=$xoopsDB->prefix('school_news');

    if($sn){
        //產生SQL修改語法
        $sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

    }else{
        //產生SQL寫入語法
        $sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
    }

    //將SQL語法送到資料庫，執行失敗會秀出訊息
    $xoopsDB->queryF($sql) or die(mysql_error());

    //儲存成功後轉向並秀出訊息
    redirect_header('main.php', 3, "發布成功！");
}


function show_form($sn){
    //利用 global 讓 $xoopsTpl 可以在函數中使用
    global $xoopsTpl,$xoopsDB;

    $all=array();
    if($sn){
        //列出指定新聞
        $sql="select * from ".$xoopsDB->prefix("school_news")." where `sn` = '{$sn}'";
        
        //送到資料庫執行
        $result=$xoopsDB->query($sql) or die(mysql_error());


        //開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
        $all=$xoopsDB->fetchArray($result);
        
        
    }

    //$out_content='Hello2!'    ;
    //$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
    //$xoopsTpl->assign('content' , $out_content);

    include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");

    //產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $all['title']) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $all['content'], 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $all['unit'],1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("sn", $sn));


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();

    $xoopsTpl->assign('content' , $main);


}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾

```


### modify   
```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";
$sn=isset($_REQUEST['sn'])?intval($_REQUEST['sn']):"";


//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news($sn);
  break;

  case "del":
  	del($sn);
  break;
  
  //修改新聞
  case "modify":
  	show_form($sn);
  break;
  
  //預設動作
  default:
  	news_list();
    show_form();
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//新聞列表
function news_list(){
	global $xoopsDB ,$xoopsTpl,$xoopsUser;

	//日期從大排到小，列出所有新聞
	$sql="select * from ".$xoopsDB->prefix("school_news")." order by `post_date` desc";


	//送到資料庫執行
	$result=$xoopsDB->query($sql) or die(mysql_error());

	//$all_data 代表所有新聞，預設為空值
	$all_data="";

	//從第0筆資料開始抓取
	$i=0;

	//開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
	while($all=$xoopsDB->fetchArray($result)){

		//抓取其中使用者編號
		$uid=$all['uid'];

		//根據uid轉換成姓名
		$uid_name=$xoopsUser->getVar('name');
		if(empty($uid_name))$uid_name=XoopsUser::getUnameFromId($uid,0);

		//將姓名塞進資料陣列中
		$all['uid_name']=$uid_name;

		//依序的把抓回的資料塞入$all_data中
		$all_data[$i]=$all;

		//資料筆數遞增
		$i++;
	}
	
var_dump($all_data);die();

	//將所有新聞內容送到樣板中
	$xoopsTpl->assign("all_data" , $all_data);



}


//刪除新聞
function del($sn){
	global $xoopsDB;

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	//產生SQL刪除語法
	$sql="delete from `{$table}` where sn='{$sn}'";

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//刪除成功後轉向並秀出訊息
	redirect_header('main.php', 3, "刪除成功！");
}



//儲存新聞
function save_news($sn){
    global $xoopsDB ,$xoopsUser;
    //利用$xoopsUser使用者物件抓取登入者的使用者編號
    $uid=$xoopsUser->uid();

    //將資料表套用前置字串
    $table=$xoopsDB->prefix('school_news');

    if($sn){
        //產生SQL修改語法
        $sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

    }else{
        //產生SQL寫入語法
        $sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
    }

    //將SQL語法送到資料庫，執行失敗會秀出訊息
    $xoopsDB->queryF($sql) or die(mysql_error());

    //儲存成功後轉向並秀出訊息
    redirect_header('main.php', 3, "發布成功！");
}


function show_form($sn){
    //利用 global 讓 $xoopsTpl 可以在函數中使用
    global $xoopsTpl,$xoopsDB;

    $all=array();
    if($sn){
        //列出指定新聞
        $sql="select * from ".$xoopsDB->prefix("school_news")." where `sn` = '{$sn}'";
        
        //送到資料庫執行
        $result=$xoopsDB->query($sql) or die(mysql_error());


        //開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
        $all=$xoopsDB->fetchArray($result);
        
        
    }

    //$out_content='Hello2!'    ;
    //$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
    //$xoopsTpl->assign('content' , $out_content);

    include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");

    //產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $all['title']) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $all['content'], 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $all['unit'],1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("sn", $sn));


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();

  $xoopsTpl->assign('content' , $main);


}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾

```


### templates/school_news_adm_main.html   

```
<!--若要套用bootstrap，請載入以下這三行-->
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/bootstrap/css/bootstrap.css" />
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/bootstrap/css/bootstrap-responsive.css" />
<link rel="stylesheet" type="text/css" media="screen" href="<{$xoops_url}>/modules/tadtools/css/xoops_adm.css" />

<h1>新聞列表</h1>

<table class="table table-striped table-bordered table-hover">
<tr>
  <th>發布日期</th>
  <th>新聞標題</th>
  <th>發布單位</th>
  <th>發布者</th>
  <th>功能</th>
</tr>
<{foreach from=$all_data item=news}>
  <tr>
    <td><{$news.post_date}></td>
    <td><{$news.title}></a></td>
    <td><{$news.unit}></td>
    <td><{$news.uid_name}></td>
    <td>
      <a href="main.php?op=del&sn=<{$news.sn}>" class="btn btn-danger btn-mini">刪除</a>
      <a href="main.php?op=modify&sn=<{$news.sn}>" class="btn btn-warning btn-mini">修改</a>
    </td>
  </tr>
<{/foreach}>
</table>
<{$bar}>

<{$content}>
```

### bar 功能

```php
<?php
/*
main.php 是模組後台的主要內容頁面（入口）。
但並不一定要叫做 main.php ，您愛命名為什麼都行，只要 menu.php 設定好就好。
*/

/*------------------ 檔頭（引入檔案） ------------------*/
//使用樣板檔
$xoopsOption['template_main'] = "school_news_adm_main.html";
//引入XOOPS前台檔案檔頭（必要）
include 'header.php';
//引入共同檔案設定檔（必要）
include_once "../function.php"; //引入自訂的共同函數檔


/*------------------ 流程判斷（告訴程式現在要做什麼） -----------------*/

//$op 為XOOPS常用之動作變數，用來告知程式欲執行之動作
$op=isset($_REQUEST['op'])?$_REQUEST['op']:"";
$sn=isset($_REQUEST['sn'])?intval($_REQUEST['sn']):"";


//判斷目前動作該執行哪一個
switch($op){
  //當 $op 的值等於「動作1」時，欲執行的動作
  case "save_news":
   save_news($sn);
  break;

  case "del":
  	del($sn);
  break;
  
  //修改新聞
  case "modify":
  	show_form($sn);
  break;
  
  //預設動作
  default:
  	news_list();
    show_form();
  break;
}

/*------------------ 所有函數（實際執行動作） ------------------*/
//新聞列表
function news_list(){
	global $xoopsDB ,$xoopsTpl,$xoopsUser;

	//日期從大排到小，列出所有新聞
	$sql="select * from ".$xoopsDB->prefix("school_news")." order by `post_date` desc";

	//getPageBar($原sql語法, 每頁顯示幾筆資料, 最多顯示幾個頁數選項);
	$PageBar=getPageBar($sql,3,$page_num);
	$bar=$PageBar['bar'];
	$sql=$PageBar['sql'];
	$total=$PageBar['total'];

	//送到資料庫執行
	$result=$xoopsDB->query($sql) or die(mysql_error());

	//$all_data 代表所有新聞，預設為空值
	$all_data="";

	//從第0筆資料開始抓取
	$i=0;

	//開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
	while($all=$xoopsDB->fetchArray($result)){

		//抓取其中使用者編號
		$uid=$all['uid'];

		//根據uid轉換成姓名
		$uid_name=$xoopsUser->getVar('name');
		if(empty($uid_name))$uid_name=XoopsUser::getUnameFromId($uid,0);

		//將姓名塞進資料陣列中
		$all['uid_name']=$uid_name;

		//依序的把抓回的資料塞入$all_data中
		$all_data[$i]=$all;

		//資料筆數遞增
		$i++;
	}
	
//var_dump($all_data);die();

	//將所有新聞內容送到樣板中
	$xoopsTpl->assign("all_data" , $all_data);

	//將換頁工具列送到樣板中
	$xoopsTpl->assign("bar" , $bar);


}


//刪除新聞
function del($sn){
	global $xoopsDB;

	//將資料表套用前置字串
	$table=$xoopsDB->prefix('school_news');

	//產生SQL刪除語法
	$sql="delete from `{$table}` where sn='{$sn}'";

	//將SQL語法送到資料庫，執行失敗會秀出訊息
	$xoopsDB->queryF($sql) or die(mysql_error());

	//刪除成功後轉向並秀出訊息
	redirect_header('main.php', 3, "刪除成功！");
}



//儲存新聞
function save_news($sn){
    global $xoopsDB ,$xoopsUser;
    //利用$xoopsUser使用者物件抓取登入者的使用者編號
    $uid=$xoopsUser->uid();

    //將資料表套用前置字串
    $table=$xoopsDB->prefix('school_news');

    if($sn){
        //產生SQL修改語法
        $sql="update `{$table}` set `title`='{$_POST['title']}', `content`='{$_POST['content']}', `unit`='{$_POST['unit']}', `post_date`=now() where sn='{$sn}'";

    }else{
        //產生SQL寫入語法
        $sql="insert into `{$table}` (`title`, `content`, `unit`, `uid`, `post_date`) values('{$_POST['title']}' , '{$_POST['content']}' , '{$_POST['unit']}' , '{$uid}' , now() )";
    }

    //將SQL語法送到資料庫，執行失敗會秀出訊息
    $xoopsDB->queryF($sql) or die(mysql_error());

    //儲存成功後轉向並秀出訊息
    redirect_header('main.php', 3, "發布成功！");
}


function show_form($sn){
    //利用 global 讓 $xoopsTpl 可以在函數中使用
    global $xoopsTpl,$xoopsDB;

    $all=array();
    if($sn){
        //列出指定新聞
        $sql="select * from ".$xoopsDB->prefix("school_news")." where `sn` = '{$sn}'";
        
        //送到資料庫執行
        $result=$xoopsDB->query($sql) or die(mysql_error());


        //開始陸續抓回資料，一次僅能抓一筆，故用 while 才能抓出所有資料
        $all=$xoopsDB->fetchArray($result);
        
        
    }

    //$out_content='Hello2!'    ;
    //$xoopsTpl->assign("樣板標籤" , "欲呈現的內容");
    //$xoopsTpl->assign('content' , $out_content);

    include_once(XOOPS_ROOT_PATH."/class/xoopsformloader.php");

    //產生一個表單
  $form = new XoopsThemeForm('新聞編輯表單', 'name', 'main.php', 'post', 1 , '新聞編輯表單');

  //把文字框元件加入表單中
  $form->addElement(new XoopsFormText('新聞標題', 'title', 60 , 255 , $all['title']) , 1);

  //把大量文字框元件加入表單中
  $form->addElement(new XoopsFormTextArea ("新聞內容", "content", $all['content'], 5, 50));

  //建立一個下拉選單元件
  $select = new XoopsFormSelect ("所屬單位", "unit", $all['unit'],1);

  //建立多個選項
  $options["教導處"]="教導處";
  $options["總務處"]="總務處";
  //加入多個選項到下拉選單元件
  $select->addOptionArray($options);
  //把下拉選單元件加入表單中
  $form->addElement($select , 1);


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("sn", $sn));


  //建立一個隱藏元件
  $form->addElement(new XoopsFormHidden ("op", "save_news"));

  //建立一個送出按鈕
  $form->addElement(new XoopsFormButton ("", "", "送出", "submit"));
  //將表單轉換成為網頁語法
  $main=$form->render();

    $xoopsTpl->assign('content' , $main);


}




/*------------------ 檔尾（輸出內容到樣板） ------------------*/
include "footer.php"; //XOOPS檔尾

```