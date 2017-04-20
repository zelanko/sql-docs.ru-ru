>[!IMPORTANT]
>После отработки отказа ресурса вручную вам необходимо удалить ограничение расположения, которое автоматически добавляется во время перемещения.

### <a name="remove-the-location-constraint"></a>Удаление ограничения расположения

При перемещении вручную с помощью команды `move` добавляется ограничение расположения для размещения ресурса на новом целевом узле. Чтобы увидеть новое ограничение, после перемещения ресурса вручную выполните следующую команду:

```bash
sudo pcs constraint --full
```

Расположение нужно удалить, чтобы гарантировать последующие успешные перемещения, включая автоматический переход на новый ресурс. 

Чтобы удалить ограничение, выполните приведенную ниже команду, где `ag_cluster-master` — это имя ресурса, который был перемещен. Замените это имя именем своего ресурса.

```bash
sudo pcs resource clear ag_cluster-master 
```

Вы также можете выполнить приведенную ниже команду для удаления ограничения расположения, где `cli-prefer-ag_cluster-master` — это код ограничения, которое необходимо удалить. `sudo pcs constraint --full` возвращает этот код.  

```bash
sudo pcs constraint remove cli-prefer-ag_cluster-master  
```

>[!NOTE]
>При автоматическом переходе на другой ресурс ограничение расположения не добавляется, поэтому очистка не требуется. 

Дополнительные сведения см. в следующих разделах:
- [Chapter 7. Managing Cluster Resources](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html) (Глава 7. Управление ресурсами кластера)
- [Clusters from Scratch. Move Resources Manually](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html) (О кластерах с нуля. Перемещение ресурсов вручную)