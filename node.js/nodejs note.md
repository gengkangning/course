#���
1. node.js����ChromeV8�����javascript���л��� 
node.js API��Ϊȫ�ֶ��� ��ͨģ��

2. linux��ʹ��git�ֿ⣺
����git
cd /wd/tools
����һ����touch a   ��ӣ�git ad
git st     git ci -m "add a"




3. 01-hello.js �ű��ļ�


3.1 ��ͷ��ע��#/usr/bin/node ���뵽�ű��ļ���


3.2 �˳� vim ����chmod u+x 01-hello-world.js(ָʾ������ļ�����node����)

3.3 ÿ������ֻ��Ҫ�����ļ�������

3.4 �ٴ����µĽű��ļ�����ʹ��cp




4. 02-hello-server.js  �����������ű��ļ�

��vi�༭����д����   ��д�ú�  �򿪷�����

�������������ip��ַ���ɴ���ҳ


�򿪷���ǽ��sudo firewall-cmd --permanent --add-port=8080/tcp


***********


#node.js APIʹ��

1. ʹ��ȫ��·���������ļ�����
����ǰʹ�õĽű��ļ�·����file_name: /home/wangding/nodejs-demo/02-global-var/01-file-dir-name.js


����ǰʹ�õĽű����ڵ�Ŀ¼·����dir_name: /home/wangding/nodejs-demo/02-global-var

ͨ����ƴ���ַ����ķ�ʽд·����



2. ����̨ console.log

./01-format.js >msg.txt �������ض���
cat err.txt ��err.txt�ļ�


��׼����

��ʱ����ʱ����ԣ�
console.time('GET-DATA')  //��������һ����Ǳ������Ե���һ��ʲô����

//���ԵĴ���

console.timeEnd('GET-DATA')  //��������




3. ���̶�����÷�
process ����ǰ����

process.argv ���Է���һ�����飬����������������Node.js����ʱ�������в�������һ��Ԫ��Ϊprocess.execPath�������Ҫ��ȡargv[0]��ֵ��μ� process.argv0���ڶ���Ԫ��Ϊ��ǰִ�е�JavaScript�ļ�·����ʣ���Ԫ��Ϊ���������в�����

eval() �����ɼ���ĳ���ַ�������ִ�����еĵ� JavaScript ���롣

childprocess������������������


process.stdin.resume();  //���̻ᱣ�ֲ��Զ��˳�(ctrl+C �˳�����)


(1)!bash
(2)ps aux �鿴��ǰϵͳ�еĽ���
(3)exit


���node -v (��ǰNode�汾��) ��Ӧconsole.log(node.version)

whoami(��ǰ�û�) ��Ӧconsole.log��process.getuid()��

id()��ID console.log(process.getgid())

pwd(��ǰ�ļ�·��) console.log(process.cwd())



##�ڴ�����
��פ�ڴ��С��console.log(process.memoryUsage().rss);
V8��̬����ѵô�С(�ܹ�)
console.log(process.memoryUsage().heapTotal);
V8��ʹ�öѵô�С
console.log(process.memoryUsage().heapUsed);
V8����İ󶨵�C++�����ϵ��ڴ�
console.log(process.memoryUsage().external);



##���env��������

ʹ�������в���  process.argv

���echo $? �鿴�˳���

process.argv[2]���˳���




##��׼���룺
process.stdin����һ�����󣬱�ʾ��׼���롣

slice() �����ɴ����е������з���ѡ����Ԫ�ء�

##������Ϣ��
process.on(�¼�������)
##������Ϣ��

###1.���������ctrl+c ctrl+z
###2.kill -2(-20)  + ���� id
###3.��дkill�ű�����Ϣ
