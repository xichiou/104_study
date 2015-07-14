
>sql/mysql.sql   

```sql
CREATE TABLE `school_news` (
  `sn` smallint(5) unsigned NOT NULL COMMENT '流水號',
  `title` varchar(255) NOT NULL COMMENT '標題',
  `content` text NOT NULL COMMENT '內容',
  `unit` varchar(255) NOT NULL COMMENT '單位',
  `uid` mediumint(8) unsigned NOT NULL COMMENT '發布者',
  `post_date` datetime NOT NULL COMMENT '發布日期'
) ENGINE=MyISAM DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;


ALTER TABLE `school_news` ADD PRIMARY KEY (`sn`);


ALTER TABLE `school_news`
MODIFY `sn` smallint(5) unsigned NOT NULL AUTO_INCREMENT COMMENT '流水號';
```
