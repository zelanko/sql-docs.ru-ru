
3. В брандмауэрах на обоих узлах кластера откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, откройте следующие порты, чтобы Pacemaker мог связываться с другими узлами в кластере.
   >
   > * Порты TCP: 2224, 3121, 21064.
   > * Порт UDP: 5405.

1. Установите пакеты Pacemaker на каждом узле.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

   

2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте одинаковый пароль на обоих узлах. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Включите и запустите службу `pcsd` и Pacemaker. Это позволит узлам повторно подключаться к кластеру после перезагрузки. Выполните следующую команду на обоих узлах:

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Создайте кластер. Чтобы создать кластер, выполните следующую команду:

   ```bash
   sudo pcs cluster auth <nodeName1> <nodeName2…> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <nodeName1> <nodeName2…> 
   sudo pcs cluster start --all
   ```
   
   >[!NOTE]
   >Если кластер был настроен ранее на тех же узлах, используйте параметр --force при выполнении команды pcs cluster setup. Обратите внимание, что это эквивалентно команде pcs cluster destroy. Службу Pacemaker необходимо включить повторно с помощью команды sudo systemctl enable pacemaker.

5. Установите агент ресурсов SQL Server для SQL Server. Выполните следующие команды на обоих узлах: 

   ```bash
   sudo yum install mssql-server-ha
   ```
