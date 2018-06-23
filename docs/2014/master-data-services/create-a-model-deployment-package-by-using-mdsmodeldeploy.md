---
title: Создание пакета развертывания модели при помощи MDSModelDeploy | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 399c6743f302bd616fe0a232527fcb5fc0af62ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192910"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Создание пакета развертывания модели при помощи MDSModelDeploy
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]для создания пакетов используется средство MDSModelDeploy. В зависимости от указанных команд, пакет может содержать:  
  
-   только объекты модели;  
  
-   объекты модели и данные.  
  
 Если необходимо развернуть пакет, содержащий только объекты модели, можно воспользоваться мастером развертывания моделей в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Дополнительные сведения см. в разделе [Создание пакета развертывания модели с помощью мастера](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
> [!NOTE]  
> Эта версия средства MDSModelDeploy не может использовать несколько гигабайт (ГБ) памяти. При создании или развертывании большие модели с помощью **модели объектов и данных** параметр «Out of Memory» или «Поток был слишком длинным» ошибки могут возникнуть. Чтобы устранить эту проблему, используйте MDS промежуточного хранения для развертывания данных; или выполните обновление до MDS 2016 или более поздней версии, которая включает обновленную версию средства MDSModelDeploy.
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
1.  Для запуска средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Такие же разрешения Windows, как у диспетчера конфигурации MDS (администратор Windows)  
  
    -   Разрешение DBA на базу данных MDS.  
  
2.  Для создания пакета с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение администратора модели MDS на модель данных.  
  
    -   Разрешение на управление интеграцией MDS.  
  
3.  Для развертывания модели с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение для функции обозревателя MDS  
  
    -   Разрешение для функции управления интеграцией MDS  
  
    -   Разрешение для функции администрирования системы MDS.  
  
4.  Для перечисления моделей с помощью средства MDSModelDeploy требуются следующие основные разрешения.  
  
    -   Разрешение для функции обозревателя MDS  
  
    -   Разрешение администратора модели MDS на модель данных с тем, чтобы видеть модель в списке.  
  
 Для создания пакета модели модель должна существовать. Дополнительные сведения см. в разделе [Создание модели (службы Master Data Services)](create-a-model-master-data-services.md).  
  
 Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Создание пакета развертывания модели с помощью MDSModelDeploy  
  
1.  Откройте командную строку.  
  
2.  Перейдите к расположению файла MDSModelDeploy.exe.  
  
    -   Если службы MDS установлены в расположение по умолчанию, что файл находится в *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
    -   Если службы MDS установлены не в папку по умолчанию, найдите файл MDSModelDeploy.exe на локальном компьютере.  
  
3.  Необязательный параметр. Просмотрите параметры и справку.  
  
    -   Чтобы показать все доступные параметры, введите `MDSModelDeploy` и нажмите клавишу ВВОД.  
  
    -   Чтобы вывести справку для параметра, введите следующую строку, где *OptionName* — имя параметра: `MDSModelDeploy help OptionName`.  
  
4.  Необязательный параметр. При наличии нескольких веб-приложений определите имя развертываемой службы, введя следующую команду, и нажмите клавишу ВВОД.  
  
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
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a>См. также  
 [Варианты развертывания модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)   
 [Развертывание моделей &#40;службы Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  