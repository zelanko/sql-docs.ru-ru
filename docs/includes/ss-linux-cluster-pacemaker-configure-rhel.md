3. На всех узлах кластера откройте в брандмауэре порты Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Если в брандмауэре нет встроенной конфигурации с высоким уровнем доступности, откройте для Pacemaker следующие порты.
   >
   > * Порты TCP: 2224, 3121, 21064.
   > * Порт UDP: 5405.

1. Установите пакеты Pacemaker на всех узлах.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте тот же пароль на всех узлах. 

   ```bash
   sudo passwd hacluster
   ```

3. Чтобы разрешить повторное присоединение узлов к кластеру после перезагрузки, включите и запустите службу `pcsd` и Pacemaker. Выполните следующую команду на всех узлах.

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
   ```
   
   >[!NOTE]
   >Если вы ранее настроили кластер на тех же узлах, нужно использовать параметр `--force` при запуске `pcs cluster setup`. Этот параметр эквивалентен запуску `pcs cluster destroy`. Чтобы повторно включить Pacemaker, запустите `sudo systemctl enable pacemaker`.

5. Установите агент ресурсов SQL Server для SQL Server. Выполните следующие команды на всех узлах. 

   ```bash
   sudo yum install mssql-server-ha
   ```
