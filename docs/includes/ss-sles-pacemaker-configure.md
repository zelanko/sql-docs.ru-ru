1. **На обоих узлах кластера создайте файлы для хранения имени пользователя и пароля SQL Server для входа Pacemaker**. Следующая команда создает и заполняет такой файл:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **У всех узлов кластера должен быть доступ друг к другу через SSH.** Таким средствам, как hb_report или crm_report (для устранения неполадок) и обозреватель журнала Hawk, не нужен пароль для доступа SSH между узлами. В противном случае они могут только собирать данные из текущего узла. Если вы используете нестандартный SSH-порт, воспользуйтесь параметром -X (см. страницу man). Например, если вы используете SSH-порт 3479, вызовите средство hb_report с помощью следующей команды:

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    Дополнительные сведения см. в [руководстве по системным требованиям и рекомендациям в документации SUSE](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html).

3. **Установите расширение высокого уровня доступности.** Чтобы установить это расширение, выполните действия, описанные в руководстве по установке и настройке в документации SUSE.
    
    [Краткое руководство по установке и настройке](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html)

4. **Установите агент ресурсов отказоустойчивого кластера для SQL Server.** Выполните следующие команды на обоих узлах:

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **Автоматически настройте первый узел.** Затем настройте запуск кластера с одним узлом. Для этого необходимо настроить первый узел — SLES1. Следуйте инструкциям, описанным в руководстве SUSE по [настройке первого узла](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node).

    После завершения настройки проверьте состояние кластера с помощью команды `crm status`.
    ```bash
    crm status
    ```

    В результатах должно быть видно, что узел SLES1 настроен.

6. **Добавьте узлы в существующий кластер.** Затем присоедините узел SLES2 к кластеру. Следуйте инструкциям, описанным в руководстве SUSE по [добавлению второго узла](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node).
    
    После завершения настройки проверьте состояние кластера с помощью команды **crm status**. Если второй узел добавлен успешно, выходные данные должны быть примерно следующими:
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** — это виртуальный кластерный ресурс IP, который настраивается в процессе первоначальной установки кластера с одним узлом.

7.  **Процедуры удаления.** Если необходимо удалить узел из кластера, используйте скрипт начальной загрузки **ha-cluster-remove**. Дополнительные сведения см. в разделе с [обзором скриптов начальной загрузки](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap).  

