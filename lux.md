## netstat

-a all
-t tcp
-u udp
-l listen
-p pid list

## ps

-A �����еĽ��̾���ʾ�������� -e ����ͬ����Ч�ã�
-a �� ��ʾ�����ն˻��µ����н��̣����������û��Ľ��̣�
-u �����û�Ϊ���Ľ���״̬ ��
x ��ͨ���� a �������һ��ʹ�ã����г���������Ϣ��
�����ʽ�滮��
l ���ϳ�������ϸ�Ľ��� PID �ĵ���Ϣ�г���
j �������ĸ�ʽ (jobs format)
-f ����һ����Ϊ�����������

## nc �������

```shell
test tcp
# nc -z -v [hostname/IP address] [port number]
test udp
# nc -z -v -u [hostname/IP address] [port number]

```

## step by step ��װubuntu

1. rufus-2.15.exe ���� ubuntu-16.04
2. sudo apt-get install openssh-server
3. sudo apt-get install openjdk-8-jdk

�����������(Samba����)
mkdir -p localdir
apt install cifs-utils
mount -t cifs //10.8.30.163/versions /var/jenkins-version -o rw

>> tail:
tail -f ѭ����ȡ
tail -n ����

>> �г����а汾��Ϣ
[root@localhost ~]# lsb_release -a

>> Systemctl  (https://linux.cn/article-5926-1.html)
Systemctl��һ��systemd���ߣ���Ҫ�������systemdϵͳ�ͷ����������
����������ʱ
systemd-analyze [blame]/������  [critical-chain]/�ؼ���
systemctl list-unit-files �г����п��õ�Ԫ
systemctl list-units �г����������е�Ԫ
systemctl --failed  �г�����ʧ�ܵ�Ԫ
systemctl is-enabled crond.service ���ĳ����Ԫ���� cron.service���Ƿ�����
systemctl status firewalld.service ���ĳ����Ԫ������Ƿ����� 
systemctl start httpd.service

systemctl restart httpd.service

systemctl stop httpd.service

systemctl reload httpd.service

systemctl status httpd.service


>> hdfs
�鿴hdfs�洢�ռ䣺
hdfs dfs -du -h / 
hdfs dfs -rmr  hdfs://node35:9000/user/anxin/check-point
docker logs xxx container_id

>> hadoop ��Ⱥ����ʱȷ�����л������û�����һ��
	��
	useradd hadoop
	passwords hadoop
	// ����sudoers
	su
	chmod 777 /etc/sudoers
	vi /etc/sudoers
		-- hadoop    ALL=(ALL)       ALL
	chmod 440 /etc/sudoers

	su hadoop
	sudo mkdir /home/hadoop
	sudo chown /home/hadoop

## �ڴ������Ų�

	free [-m -g...]
	 total        used        free      shared  buff/cache   available
Mem:       12219288     7485148      271236       27104     4462904     4311184
Swap:             0           0           0
	mem:�����ڴ� swapӲ���Ͻ���������ʹ�������ֻ��mem����ǰ����ʵ��ռ����,��û����buffers��cacheʱ���Ż�ʹ�õ�swap
	MEM -- total: �������ڴ��С  used: �ܼƷ��������ʹ�õ�����(����buff/cache)  free: δ��������ڴ�  shared: �����ڴ�(һ��ϵͳ�����õ�)
			buff/cache�� ���䵫δ��ʹ�õ�cache��buffer����
	<https://blog.csdn.net/tianlesoftware/article/details/5463790>
	

	dmidecode -t processor memory [bios, system, baseboard, chassis, processor, memory, cache, connector, slot]
	
	top -d 1(1�����һ��)  -c����ʾ������·�����ƣ�  -i(����ʵ�κ�Idle��zombie����)  -m(���´�������ɺ��˳�)
	��������     �����ȼ���				  
	PID USER      PR  NI�����ȼ�����ֵ��    VIRT������ռ�õ������ڴ�ֵ��    RES������ռ�õ������ڴ�ֵ��
	SHR������ʹ�õĹ����ڴ�ֵ�� S�����̵�״̬������S��ʾ���ߣ�R��ʾ�������У�Z��ʾ����״̬��N��ʾ�ý�������ֵ�Ǹ�����
	%CPU %MEM     TIME+ COMMAND                                                                                                                       
 3581 root      20   0  415048 266628  21956 S   6.3  2.2 512:58.32 kube-apiserver                                                                                                                
  730 root      20   0  708712  61548  16404 S   4.7  0.5 333:30.48 kubelet                                                                                                                       
 3241 root      20   0  139472  57008  15800 S   4.0  0.5 353:34.31 kube-controller  
	

	top��֧�ֵĲ�����
	 ���ո񡷣�����ˢ�¡�
	
	P������CPUʹ�ô�С��������
	
	T������ʱ�䡢�ۼ�ʱ������
	
	q���˳�top���
	
	m���л���ʾ�ڴ���Ϣ��
	
	t���л���ʾ���̺�CPU״̬��Ϣ��
	
	c���л���ʾ�������ƺ����������С�
	
	M������ʹ���ڴ��С��������
	
	W������ǰ����д��~/.toprc�ļ���
	
	SHIFT+M �̶����ڴ�����


?	
	uptime ��ʾϵͳ����ʱ�� ���1����/5����/15���ӵ�ϵͳ����
	17:38:07 up 6 days,  1:13,  4 users,  load average: 0.32, 0.36, 0.45
	
	vmstat��ʾ
	procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
	 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
	 0  0      0 251324 477184 3994764    0    0     8    48   10   12  3  2 94  1  0
	 ���У�
	 io:
		bi - �Ӵ���ÿ���ȡ�Ŀ�����blocks/s��
		bo - ÿ��д�����̵Ŀ�����blocks/s��
	 cpu:
		us - �û�����ռcpu����
		sy - ϵͳռ�ñ���
		id - ����ʱ�����
		wa - cpu�ȴ�δ���Ĵ���IOʱ�����
		
	iostat ����ͳ��CPU��ʹ�������tty�豸��Ӳ�̺�CD-ROM��I/0��

## GREP��ѯ�������

kubectl logs spark-et-driver-savoir | grep 'a\|b'
kubectl logs -n savoir savoir-recv2-d55c84956-lwt47 --tail 100000 | egrep 'savoir_data.*d931eb76-7703-4d8c-a240-8158a02ceeae.*"result":{"code":3002'
netstat -an | grep -E "ESTABLISHED|WAIT"

ʹ�÷�ʽ��egrep [OPTIONS] PATTERN [FILE...] 

����grep -E [OPTIONS] PATTERN [FILE...]

����-i�������ַ��Ĵ�Сд
����-o������ʾƥ�䵽���ַ�������
����-v����ʾ����ģʽƥ�䵽����
����-q����Ĭģʽ����������κ���Ϣ
����-A #����ʾ��ģʽƥ����м����#��
����-B #����ʾ��ģʽƥ����м���ǰ#��
����-C #����ʾ��ģʽƥ����м���ǰ���#��
����-G:֧�ֻ���������ʽ


## chmod �÷�
	u -- User �ļ���Ŀ¼��ӵ����
	g -- Group ����Ⱥ��
	o -- Other
	a -- ȫ���û�
	r -- ��ȡȨ�ޣ����ִ���4
	w -- д��Ȩ�ޣ����ִ���2
	x -- ִ�л��л�Ȩ�ޣ����ִ���1
	- -- �����κ�Ȩ�ޣ����ִ���0
	s -- ���⹦��˵��������ļ���Ŀ¼��Ȩ��
	-R �ݹ鴦��
	chmod u+x f01 // ����ӵ���ߵĿ�ִ������
	chmod u=rwx,g=rw f01
	chmod 764 f01
	
	- rw- r-- r-- 
	��һ���ַ�"-"��ʾ��ͨ�ļ� "d"��ʾĿ¼
	��������ֱ�Ϊ u/g/o �û���Ȩ��


## ����/ɾ�� ָ�����ڵ��ļ�
	find .  -type f  -name *.*  -mtime +10  -exec rm {} \;
	. ��ǰĿ¼
	-type f �����ļ�
	-name *.log �������ƺ�׺log���ļ�
	-mtime +180  ��ѯ180����ǰ���ļ�
	find . -type f -mtime -180 -exec ls -l {} \; | more
	find . -newermt '2016-11-03' ! -newermt '2016-11-04' -exec ls -l {} \;
	
	find . -type d -ctime +10 | xargs rm -rf;
	ɾ���޸�ʱ�䳬��10��������ļ��� ���ȼ��� find /path/to/base/dir/* -type d -ctime +10 -exec rm -rf {} \;��
	
	// ��versionĿ¼ִ��
	find . -type d -mindepth 1 -maxdepth 2  -ctime +10 | xargs rm -rf
	...TO LERN MORE
	
	>>
	-amin <����> ������ָ��ʱ��������ȡ�����ļ���Ŀ¼
	-anewer <�ο��ļ���Ŀ¼> �������ȡʱ�佻ָ���ļ���Ŀ¼�Ĵ�ȡʱ����µ�
	-atime<24Сʱ��>��������ָ��ʱ��������ȡ�����ļ���Ŀ¼����λ��24Сʱ���㣻
	-depth Ŀ¼���
	-daystart �ӱ��տ�ʼ����ʱ��
	-empty Ѱ�ҿ��ļ����ļ���
	-name "*.txt" �����ļ���
	-iname "*.txt" ͬ�ϣ����Դ�Сд
	find . -type f -size +10k ��������10KB���ļ�
	find . -maxdepth 3 -type f ��������������Ϊ3
	find . -mindepth 2 -type f ��������Ⱦ��뵱ǰĿ¼����2����Ŀ¼�������ļ�
	find /usr/ -path "*local*" ·��ƥ��
	find . -regex ".*\(\.txt\|\.pdf\)$" ����������ʽƥ���ļ�·��

## ���̿ռ� �� ���Ҵ��ļ�
```bash
find / -type f -size +200M 2>/dev/null|xargs du -shm|sort -nr|awk '{print $2}'|ls -l

ls -ll
du -h �Cmax-depth=1 *  ���Բ鿴��ǰĿ¼�¸��ļ����ļ��еĴ�С
du -sh ��ѯ��ǰĿ¼�ܴ�С

```


?	
## ��̨��������
  *nohup �������ssh���̹رգ���̨nohup����Ҳ�ᱻ�ر�
  ����ʹ�� screen
  apt-get install screen
  > screen ��Enter�������µ�screen
	> ���µ�screen����ʹ��nohup������ֱ���������������ǵĽ���
	> Ctrl A + D �˳�
	> ��ʾ [detached from 8377.pts-12.node35]
  > �г���ǰ�û�����screen -ls
  > ��������screen -r 8377.pts-12.node35

## �رս�������
https://serverfault.com/questions/684771/best-way-to-disable-swap-in-linux
	1. Identify configured swap devices and files with cat /proc/swaps.
	2. Turn off all swap devices and files with swapoff -a.
	3. Remove any matching reference found in /etc/fstab.
	4. Optional: Destroy any swap devices or files found in step 1 to prevent their reuse. Due to your concerns about leaking sensitive information, you may wish to consider performing some sort of secure wipe.
	
	1. run swapoff -a: this will immediately disable swap
	2. remove any swap entry from /etc/fstab
	3. reboot the system. If the swap is gone, good. If, for some reason, it is still here, you had to remove the swap partition. Repeat steps 1 and 2 and, after that, use fdisk or parted to remove the (now unused) swap partition. Use great care here: removing the wrong partition will have disastrous effects!
	4. reboot

## xshellʹ��
	���������������Ĭ������ΪUTF-8
	������������������ɫ(��ʶ����Ҫ������)
	sudo apt install lrzsz��װ�����ʵ���ļ����䣨��ק�ϴ�/rz �ϴ�/sz ���أ�

## git Permission denied (github)
	ssh-keygen
	copy C:\Users\yww08/.ssh/id_rsa.pub ����
	github.com >personal settings>SSH > New SSH Key
	[ref](https://stackoverflow.com/questions/2643502/how-to-solve-permission-denied-publickey-error-when-using-git)


?	
## ���� alias

	alias ka='kubectl get pods -n anxinyun'
	alias
	
	��~/.bashrc�ļ������
	alias ka='kubectl get pods -n anxinyun -o wide'
	alias kla='kubectl logs -n anxinyun '
	alias ksa='kubectl get services -n anxinyun -o wide'
	alias klat='kubectl logs -n anxinyun --tail 1000'
	alias kda='kubectl delete pod -n anxinyun'
	alias ks='kubectl get pods -n savoir -o wide'
	alias kss='kubectl get services -n savoir -o wide'
	alias kls='kubectl logs -n savoir '
	alias klst='kubectl logs -n savoir --tail 1000'

## Linux <> Windows �ļ�����
	rz 
	sz file

## ElasticSearch���ݵ���
	https://www.npmjs.com/package/elasticdump
	
	npm install elasticdump -g
	
	elasticdump \
  --input=http://iota-m2:9200/aqi_division_hour \
  --output=/home/anxin/tools/aqi_division_hour_mapping.json \
  --type=mapping

  elasticdump \
  --input=http://production.es.com:9200/my_index \
  --output=http://staging.es.com:9200/my_index \
  --type=analyzer
elasticdump \
  --input=http://production.es.com:9200/my_index \
  --output=http://staging.es.com:9200/my_index \
  --type=mapping

  curl -X PUT 'http://172.16.3.5:9200/shining_index' -d@/data/shining_index_mapping.json

  

 ## Ubuntu 16.04 ��װjenkins
 https://www.jianshu.com/p/845f267aec52

������������
systemctl status jenkins.service
����
Failed to start LSB: Start Jenkins at boot time

>> �鿴�Ƿ�װjdk
>> �Ƿ�˿ں��ض����޸�jenkins�˿� https://blog.csdn.net/csfreebird/article/details/9033443

jenkins�ϳ�������go��Ŀ��
https://blog.csdn.net/aixiaoyang168/article/details/82965854

## HDFS
Missing Blocks
1 hdfs fsck -list-corruptfileblocks
1 hdfs fsck / | egrep -v '^\.+$' | grep -v eplica
�鿴����ĳһ���ļ������
1 hdfs fsck /path/to/corrupt/file -locations -blocks -files

�������
����ļ�����Ҫ������ֱ��ɾ�����ļ�(hdfs fsck -delete)����ɾ�������¸���һ�ݵ���Ⱥ��
�������ɾ������Ҫ�������������ҵ���������̨�����ϣ�Ȼ�󵽴˻����ϲ鿴��־��


hadoop fs  -stat %r /anxinyun


163DORCKER
sudo nsenter --target `sudo docker inspect -f {{.State.Pid}} a699a640d325` --mount --uts --ipc --net --pid 
chown 1000:1000 /var/run/docker.sock

## k8s����ɾ��pod
kubectl get pods -n savoir| grep savoir-jupyter | awk '{print $1}' | xargs kubectl delete pod -n savoir

## mosquitto����
	ps -ef | grep mosq
	
	/etc/mosquitto/mosquitto.conf

## ambari �ڵ��ϵķ��� ��ʾ������ʧ

����ambari����
��������� service ambari-agent restart

