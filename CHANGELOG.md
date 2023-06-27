## 版本更新记录

### v9.1.0 2020-3-8

- 网页版：
  - 新增`相册模块`，网址为 [Grayson's Album](http://album.grayson.top)，主要展示自己生活中的摄影照片，用相机记录生活的美好

- 爬虫：
  - `CommonUtils.py`中新增方法：
    - `download_album(album_name, save_path="/Volumes/MyPassport/MyPictures")`：下载相册中的照片
    - `modify_album_cover()`：修改相册封面
    - `change_photo_suffix()`：修改照片中的地址后缀
    - `upload_image_single(source_base_path, album_name, photo_name, target_base_path=IMAGES_PATH)`：上传单个文件夹中的图片
    - `upload_image_list(source_base_path='/Volumes/MyPassport/MyPictures/Qzone', target_base_path=IMAGES_PATH)`：上传多个文件夹中的图片
    - `get_image_info(image_item, path)`：获取照片信息
    - `download_images(url)`：下载图片到本地

### v8.2.0 2020-2-17

- 爬虫：
  - `CommonUtils.py`中新增方法：
    - `get_field_list(file_path, file_name)`：获取mongodb的字段名称列表
    - `write_data_to_csv(file_path, file_name, field_list, data_list, date)`：将数据以csv格式写入文件
    - `mongo_to_local(day_delta=0, hour_delta=0, minute_delta=0, second_delta=0, format=format, target_date=None)`：将mongodb中的数据下载到本地(csv)
    - `get_requests()`：获取requests对象
    - `parse_unicode(unicode_str, encoding='utf-8')`：将unicode字符串解析成指定格式的字符串
    - `handle_with_video_info_list(video_info_list)`：对video_info_list进行处理，返回相应的资源列表(xunleiyy)
    - `handle_with_mac_url(source_name_list, mac_url)`：对mac_url进行处理，返回相应的资源列表(ziyuan88ys)

### v8.1.0 2020-2-8

- 爬虫：
  - 修复优酷视频爬虫问题
  - `CommonUtils.py`中新增方法：
    - ```mongo_to_es(day_delta=0, hour_delta=0, minute_delta=0, second_delta=0, format=format)```：将mongodb中的数据同步到elasticsearch

### v7.1.0 2020-1-31

- 移动版：
  - 解决播放视频时自动锁屏的问题

### v6.3.0 2019-12-8

- 网页版：
  - 掌上影视、电视、戏曲、小品首页核心内容实现静态化
  - 新增定时器，每隔10分钟渲染一下首页核心内容
  - `CommonUtils.java`中新增方法：
    - `public void saveHtml(String url, String filePath, String fileName)`：获取网页内容并保存到本地
    - `public String getParseUrl(String movieType, String url)`：获取解析地址
    - `public JSONArray getRecords(HttpServletRequest request, String browse_type)`：获取浏览记录
    - `public Boolean existCookie(HttpServletRequest request, String cookieName)`：判断 request 中是否存在指定名称的 cookie
    - `public static JSONObject getCookieValue(HttpServletRequest request, String cookieName)`：从 request 中获取指定名称的 cookie 的值
    - `public static List<Integer> getPages(Integer count, Integer pageIndex, Integer pageSize, Integer totalPage)`：获取页码数据
    - `public static String doPost(String url, JSONObject json)`：执行POST请求
    - `public JSONObject doGet(String url)`：执行GET请求
- 服务器脚本：
  - 新增脚本：
    - `start_render.sh`：将最新渲染后的首页核心内容放入jar包中指定位置

### v6.2.0 2019-12-6

- 图片服务器：
  - 新增图片服务器项目：
    - 项目名称：`ImageWeb`
    - 接口地址：`http://images.grayson.top`
  - 将原先下载的本地图片移动到图片服务器中
- 移动网页服务器：
  - 新增移动网页服务器项目：
    - 项目名称：`MobileWeb`
    - 接口地址：`http://m.grayson.top`
- 爬虫：
  - `CommonUtils.py`中新增方法：
    - `def modify_src()`：修改图片地址(将包含/public...的地址修改为images.grayson.top的形式)
    - `generate_uuid()`：生成uuid
    - `download_film_image()`：下载影视图片
    - `download_image(db_utils, url_list, thread_num=10)`：多线程下载图片
    - `combine_piece()`：合并名称播放地址的小品
    - `modify_piece_type(type, type2)`：修改小品的类型
    - `get_today()`：获取今天的日期

### v6.1.0 2019-12-5

- 爬虫：
  - 新增采集资源师将图片保存到本地的功能
- 备份数据库

### v5.7.0 2019-11-22

- 更新`README.md`文件，新增`部署方法`、`使用说明`
- 备份数据库

### v5.6.0 2019-11-18

- 网页版：
  - 部分页面实现异步加载数据
- 备份数据库

### v5.5.0 2019-11-17

- 网页版：
  - 新增移动端适配，移动浏览器访问网站时自动重定向到```m.grayson.top```
- 备份数据库

### v5.4.0 2019-11-14

- 爬虫：
  - 修复戏曲爬虫部分逻辑
- 移动端：
  - 修复戏曲详情模块和播放模块相关显示问题
- 网页版：
  - 修复戏曲和小品相关显示问题
- 备份数据库

### v5.3.0 2019-11-13

- 爬虫：
  - 新增小品吧(```piece3```)爬虫，网址为：http://www.xiaopin8.cc
  - 新增小品网(```piece4```)爬虫，网址为：http://www.xiaopin.tv
- 备份数据库

### v5.3.0 2019-11-9

- 新增推荐系统模块，该推荐系统是基于内容的协同过滤算法实现的，用于计算影视相关性矩阵，然后根据用户的浏览记录为用户推荐相似的影视
  - ```CommonUtils.py```中新增方法：
    - ```distinct(items,key)```：对字典列表根据指定的key去重
    - ```get_yesterday()```：获取昨天的日期
    - ```get_equal_rate_1(str1, str2)```：计算两个字符串的相似度
    - ```get_recommendations(movie_type, type)```：计算影视的相似度
    - ```calculate_euclidean(movie1,movie2, types, weight_types_dic)```：计算两个物品的相似度(欧几里德距离)
- 爬虫：
  - 新增40资源站(```ziyuan40```)爬虫，网址为：[https://jx40.net](https://jx40.net/)
- 移动端
  - 版本更新到 ```3.2.0```
  - 新增影视推荐功能
- 网页版
  - 新增影视推荐功能
- API接口
  - 新增相关接口：
    - ```/recommendations/get/user```：获取推荐的数据(用户名)
    - ```/recommendations/get```：获取推荐的数据(影视)
- 备份数据库

### v5.2.0 2019-11-7

- 爬虫：
  - `CommonUtils.py`新增方法：
    - ```modify_update_status()```：修改影视的更新状态
- 移动端
  - 版本更新到 ```3.1.0```
  - 新增反馈功能
- 网页版
  - ```www.grayson.top```：中新增反馈功能
- API接口
  - 新增相关接口：
    - ```/feedback/get/all```：获取所有反馈信息
    - ```/feedback/add```：添加反馈信息
    - ```/feedback/reply```：回复反馈信息
- 备份数据库

### v5.1.0 2019-11-3

- 爬虫：
  - 修改腾讯视频(```tencent```)、优酷视频(```youku```)、爱奇艺视频(```iqiyi```)爬虫逻辑，使数据爬取更为快速
  - `CommonUtils.py`新增方法：
    - ```reverse_type_name(type_name)```：转换影视资源类型名称，例如将1转换为01
    - ```get_year_from_name(name)```：从影视资源类型名称中获取年份
    - ```generate_app_qrcode_image()```：生成下载掌上影视APP二维码
- 备份数据库

### v4.6.0 2019-10-27

- 爬虫：
  - 完善  ```start_spiders.sh```脚本逻辑，修复已经存在的问题
  - `CommonUtils.py`新增方法：
    - ```generate_qrcode_image(url)```：根据url生成二维码
- 移动端：
  - 影视模块中新增少儿版块
  - 页面布局重新优化
  - 修改视频解析接口，解决视频播放时有广告的问题
  - 视频播放时自动横屏
  - 新增搜索记录功能
  - 戏曲和小品模块中新增全部功能
- 备份数据库

### v4.5.0 2019-10-25

- 爬虫：
  - 所有爬虫新增爬取最近数据功能，一部分爬取6页，一部分爬取2页
  - 对所有爬虫已经出现的问题进行修改
- 备份数据库

### v4.4.0 2019-10-24

- 爬虫：
  - 对所有爬虫已经出现的问题进行修改
  - ```CommonUtils.py```中新增方法：
    - ```change_src_suffix(old_suffix, new_suffix)```：修改图片中的地址后缀
    - ```get_exclude_type2_list()```：获取排除在外的影视第二类型列表
    - ```modify_movie_type2(type2_list)```：修改影视第二类型
    - ```combine_movie()```：合并名称相同的影视
    - ```exclude_piece_type2(type2)```：判断小品类型是否在被排除的类型里面
    - ```reverse_update_time(update_time)```：转换更新日期
    - ```reverse_release_date(release_date)```：转换发布日期
    - ```delete_drama_with_url_invalid()```：删除不正确播放地址的戏曲视频
- 移动端：
  - 对页面布局进行调整
  - 新增搜索记录功能
- 备份数据库

### v4.3.0 2019-10-22

- 移动端：
  - 新增播放页面，修改影视详情页面，将在影视详情页面播放改为在播放页面播放
  - 播放页面播放时自动横屏，可以在播放页面显示播放列表，不需要回到影视详情页面即可以更改影视资源
  - 搜索页面新增记录搜索记录功能
- 备份数据库

### v4.2.0 2019-10-19

- 爬虫部分：
  - 新增相声小品网爬虫(```piece2```)，网址为：https://www.verity-china.com，主要爬取一些最新的相声小品
  - 新增永久资源网爬虫(```yongjiu```)，网址为：http://www.yongjiuzy.cc，主要爬取最新的影视数据
  - 新增135资源网爬虫(```zuiyuan135```)，网址为：[http://135zy0.com](http://135zy0.com)，主要爬取最新的影视数据
  - 新增ok资源网爬虫(```ok```)，网址为：http://www.okzy.co，主要爬取最新的影视数据
  - 新增33uu资源网爬虫(```ziyuan33uu```)，网址为：http://www.156zy.co，主要爬取最新的影视数据
- ```CommonUtils.py```中新增方法：
  - ```is_exclude_type2(type2)```：判断影视第二类型是否需要排除
  - ```is_need_source(item, collection)```：判断当前资源是否需要爬取
  - ```get_type_from_type2(type2)```：根据影视第二类型type2获取第一类型type
  - ```update_src_batch(old_suffix, new_suffix)```：批量修改电视中的图片地址
- 修复爬虫和网页中部分已知问题
- 备份数据库

### v4.1.0 2019-10-18

- 爬虫部分：腾讯爬虫中新增少儿部分，新增优酷爬虫(```youku```)、爱奇艺(```iqiyi```)爬虫
- ```CommonUtils.py```中新增方法：
  - ```insert_item_to_dic(dic, key, new_key, new_value)```：向字典中添加新的元素
  - ```reverse_arr(arr)```：对数组中的元素去空格
- 修复爬虫中部分已知问题
- 备份数据库

### v3.2.0 2019-9-30

- 爬虫部分增加了腾讯视频( ```tencent``` )，主要爬取电影、电视剧、综艺、动漫
- 电视爬虫接口改为好趣网([http://www.haoqu.net](http://www.haoqu.net/))
- 修复了爬虫部分的其他一些已知问题
- 新增掌上( ```Web``` )项目，包括掌上官网(http://www.grayson.top)、掌上影视(http://film.grayson.top)、掌上电视(http://tv.grayson.top)、掌上戏曲(http://drama.grayson.top)、掌上小品(http://piece.grayson.top)
- 备份数据库

### v3.1.0 2019-9-25

- 移动版更换相关视频解析接口
- 移动版解决其它已知问题
- 新增爬取最大资源网(http://www.zuidazy1.net/)、酷云资源网 (http://www.kuyunzy1.com/)相关爬虫
- 备份数据库

### v2.1.0 2019-7-2

- 移动版对影视、电视、戏曲、小品模块增加缓存功能
- 移动版解决其它已知问题
- 备份数据库

### v1.10.0 2019-7-1

- 移动版修复刷新时推荐数据不能更新的问题
- 移动版解决其它已知问题

### v1.9.0 2019-7-1

- 移动版在影视、电视、戏曲、小品模块增加猜你喜欢功能
- 移动版解决其它已知问题
- 改进爬虫代码、提升数据爬取效率
- 备份数据库

### v1.8.0 2019-6-30

- 移动版修改接口地址
- 修复移动版其它已知问题
- 备份数据库

### v1.7.0 2019-6-28

- 移动版新增双击退出功能
- 修复移动版其它已知问题
- 备份数据库

### v1.6.0 2019-6-28

- 移动版新增小品模块
- 移动版实现浏览记录功能
- 解决移动版部分已知问题
- 爬虫新增小品模块
- 爬取小品数据
- 解决爬虫部分已知问题
- 接口新增获取所有小品数据、获取小品详情、获取小品类型、添加浏览记录、获取浏览记录接口
- 更新影视、电视、戏曲、小品数据
- 备份数据库

### v1.5.0 2019-6-9

- 移动版功能完善
- 爬虫新增根据关键词爬取内容的功能
- 爬虫已知问题的修复
- 数据库的备份

### v1.4.0 2019-6-8

- 移动版新增戏曲功能
- 修复戏曲爬虫问题
- 备份数据库

### v1.3.0 2019-6-6

- 修复戏曲爬虫问题
- 新增戏曲类型爬虫
- 新增掌上影视小程序项目，并完成相应功能
- 备份数据库

### v1.2.0 2019-6-3

- 增加戏曲爬虫
- 增加备份数据库脚本，并将数据库进行备份

### v1.1.0 2019-5-31

- 修复影视爬虫爬取数据中影视名称、地区、简介为数组的问题
- 增加判断```python```类型的方法

### v1.0.0 2019-5-28

- 完成影视接口代码的编写、测试及运行
- 完成移动端代码的编写、测试及运行
- 完成影视爬虫代码的编写、测试及运行
