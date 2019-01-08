3. В брандмауэрах на всех узлах кластера откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Если в брандмауэре нет встроенной конфигурации высокого уровня доступности, откройте следующие порты для Pacemaker.
   >
   > * TCP: Порты с кодом 2224, 3121, 21064.
   > * UDP: Порт 5405.

1. Установите пакеты Pacemaker на всех узлах.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте на всех узлах один и тот же пароль. 

   ```bash
   sudo passwd hacluster
   ```

3. Чтобы разрешить повторное присоединение узлов к кластеру после перезагрузки, включите и запустите службу `pcsd` и Pacemaker. Выполните на всех узлах следующую команду.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Создайте кластер. Чтобы создать кластер, выполните следующую команду:

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2> <node3> 
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >Если кластер был ранее настроен ранее на тех же узлах, при выполнении команды `pcs cluster setup` используйте параметр `--force`. Этот параметр эквивалентен запуску `pcs cluster destroy`. Чтобы повторно включить Pacemaker, запустите `sudo systemctl enable pacemaker`.

5. Установите агент ресурсов SQL Server для SQL Server. Выполните следующие команды на всех узлах. 

   ```bash
   sudo yum install mssql-server-ha
   ```
