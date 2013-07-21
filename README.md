shanghai_subway_find-web
========================

基于B/S模型的上海铁路查询系统(最短路径，且此路径上的最少换乘)
  
  服务器端的程序是用cgi来实现的。
  apache2 下架设虚拟主机。首先在/etc/apache2/sites-available/下复制default文件，
  并取名为你所想要的虚拟域名（如：www.love.com)，取域名后就可用域名来访问你的网站了，
  而不再需要输入localhost/ try.html ，就直接用www.love.com/try.html，这样看起来比较正
  式。复制好后，用编辑器打开修改里面的内容：修改服务器名ServerName www.love.com，然
  后修改根目录：DocumetRoot /home/web (这个修改是自愿的，不改也可以，就是以后需要把你
  写的网页什么的都要放到默认目录下,一般(/var/www/)), 在往下看，有一个 ScriptAlias /cgi-bin/  /usr/lib/cgi-bin/
  <Director “/usr/lib/cgi-bin”>
  这个cgi-bin/目录是用来存放你的cgi程序的(CGI(Common Gateway Interface)是HTTP服务器与你的或其它机器
  上的程序进行“交谈”的一种工具，其程序须运行在网络服务器上。通俗的来讲就是，如果有一个cgi 程序的运行
  结果可在网页上显示，而cgi应用程序可以由大多数的编程语言编写，如Perl（Practical Extraction and Report Language)、
  C\C++、Java 和Visual Basic等)，你也可更改其他目录,但上面两个蓝色路径都要更改,因此可改为如：”/home/web/cgi-bin/”。
  然后退出保存, 在终端输入: a2ensite www.love.com ,这样就会把你的域名配置映射到/sites-enabled/ . 之后执行sudo gedit /etc/hosts
  在服务器默认分配的本机ip(一般127.0.0.1)下面，添加另一ip(127.0.0.2/127.0.3等本机保留ip都行，也可以是你本机真是ip)。
  修改之后就是重启apache服务器了：sudo service apache2 restart，到此你的apache虚拟主机就建好了.
  此程序中的数据是保存在mysql数据库中的，数据就是那几个txt文本文件，只要导入数据库中就行， 但在建立表时要把表的名字和txt文本文件的名字一样，不然的话就要修改程序中所读的表的名字为你 所新起的名字。
  导入txt文本中的数据,以及其他mysql中的设置可参考:
http://blog.chinaunix.net/uid-28308371-id-3808749.html
