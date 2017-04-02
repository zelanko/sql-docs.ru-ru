---
title: "Создание пакета развертывания модели при помощи MDSModelDeploy | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# Создание пакета развертывания модели при помощи MDSModelDeploy
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]для создания пакетов используется средство MDSModelDeploy. В зависимости от указанных команд, пакет может содержать:  
  
-   только объекты модели;  
  
-   объекты модели и данные.  
  
 Если необходимо развернуть пакет, содержащий только объекты модели, можно воспользоваться мастером развертывания моделей в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Дополнительные сведения см. в разделе [Создание пакета развертывания модели с помощью мастера](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
1.  Для запуска средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Такие же разрешения Windows, как у диспетчера конфигурации MDS (администратор Windows)  
  
    -   Разрешение DBA на базу данных MDS.  
  
2.  Для создания пакета с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение администратора модели MDS на модель данных.  
  
    -   Разрешение для функциональной области MDS ImportExport.  
  
3.  Для развертывания модели с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение для функции обозревателя MDS  
  
    -   Разрешение для функции администрирования системы MDS.  
  
4.  Для перечисления моделей с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение для функции обозревателя MDS  
  
    -   Разрешение администратора модели MDS на модель данных с тем, чтобы видеть модель в списке.  
  
 Для создания пакета модели модель должна существовать. Дополнительные сведения см. в разделе [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md).  
  
 Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Создание пакета развертывания модели с помощью MDSModelDeploy  
  
1.  Откройте командную строку администратора.  
  
2.  Перейдите к расположению файла MDSModelDeploy.exe.  
  
    -   Если службы MDS установлены в папку по умолчанию, то этот файл находится в каталоге *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
    -   Если службы MDS установлены не в папку по умолчанию, найдите файл MDSModelDeploy.exe на локальном компьютере.  
  
3.  Необязательно. Просмотрите параметры и справку.  
  
    -   Чтобы показать все доступные параметры, введите `MDSModelDeploy` и нажмите клавишу ВВОД.  
  
    -   Чтобы вывести справку для параметра, введите следующую строку, где *OptionName* — имя параметра: `MDSModelDeploy help OptionName`.  
  
4.  Необязательно. При наличии нескольких веб-приложений определите имя развертываемой службы, введя следующую команду, и нажмите клавишу ВВОД.  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     Возвращается список значений, например `MDS1, Default Web Site, MDS`. Первое значение в этом списке (в данном случае `MDS1`) необходимо для развертывания модели.  
  
5.  Чтобы создать пакет, содержащий объекты модели и данные, введите следующую строку, в которой *ModelName*, *VersionName*, *ServiceName*и *PackageName* — это имена модели, версии, службы и выходного PKG-файла соответственно:  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     Если включать данные не требуется, не указывайте параметры `-version` и `-includedata` .  
  
6.  Нажмите клавишу ВВОД. После успешного создания пакета отображается сообщение «Операция MDSModelDeploy успешно завершена».  
  
## Следующие шаги  
  
-   [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## См. также:  
 [Варианты развертывания модели (службы Master Data Services)](../master-data-services/model-deployment-options-master-data-services.md)   
 [Развертывание моделей (службы Master Data Services)](../master-data-services/deploying-models-master-data-services.md)  
  
  