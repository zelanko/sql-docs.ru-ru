---
title: Развертывание пакета развертывания модели при помощи MDSModelDeploy | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e99859dcdfcc2061622e955399b6d7bdac8bcbf4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095035"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Развертывание пакета развертывания модели при помощи MDSModelDeploy
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]средство MDSModelDeploy используется для развертывания пакетов, содержащих:  
  
-   только объекты модели;  
  
-   объекты модели и данные.  
  
 Если необходимо развернуть пакет, содержащий только объекты модели, можно воспользоваться мастером развертывания моделей в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Дополнительные сведения см. в статье [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md).  
  
> [!IMPORTANT]  
>  Пакеты могут быть развернуты только в выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , в котором они были созданы. Это означает, что пакеты, созданные в среде [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] , не могут быть развернуты в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] или более поздних версиях.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** в целевой среде служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ;  
  
-   должен существовать пакет развертывания модели. Дополнительные сведения см. в статье  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
-   В среде, в которой выполняется развертывание модели, необходимо обладать правами администратора. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   При обновлении модели данных развертываемая версия не может быть **Заблокирована** или **Зафиксирована**.  
  
### <a name="to-deploy-a-model-deployment-package"></a>Развертывание пакетов развертывания модели  
  
1.  Определите, производится развертывание новой модели, копии модели или обновление скопированной ранее модели. Дополнительные сведения см. в разделе [Варианты развертывания модели (службы Master Data Services)](../../2014/master-data-services/model-deployment-options-master-data-services.md).  
  
2.  Откройте командную строку и перейдите к MDSModelDeploy.exe.  
  
    -   Если службы MDS установлены в расположении по умолчанию, средство находится в *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe  
  
    -   Если службы MDS не установлены в местоположение по умолчанию, то найдите файл MDSModelDeploy.exe на локальном компьютере.  
  
3.  Необязательный параметр. Просмотрите параметры и справку.  
  
    -   Чтобы показать все доступные параметры, введите `MDSModelDeploy` и нажмите клавишу ВВОД.  
  
    -   Чтобы вывести справку для параметра, введите следующую строку, где *OptionName* — имя параметра: `MDSModelDeploy help OptionName`.  
  
4.  Необязательный параметр. При наличии нескольких веб-приложений определите имя развертываемой службы, введя следующую команду, и нажмите клавишу ВВОД.  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     Возвращается список значений, например `MDS1, Default Web Site, MDS`. Первое значение в этом списке (в данном случае `MDS1`) необходимо для развертывания модели.  
  
5.  В зависимости от выполняемой задачи (создание модели, копирование модели или обновление модели) наберите в командной строке следующий текст и нажмите клавишу ВВОД.  
  
    -   Создание новой модели:  
  
        ```  
        MDSModelDeploy deploynew –package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   Создание копии модели:  
  
        ```  
        MDSModelDeploy deployclone –package PackageName  
        ```  
  
    -   Обновление существующей модели и ее данных:  
  
        ```  
        MDSModelDeploy deployupdate –package PackageName –version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  Если средство MDSModelDeploy используется для обновления существующей модели и ее данных и пакет не содержит сущность, атрибут или элемент, имеющиеся в целевой модели, MDSModelDeploy не удаляет из модели эту сущность, атрибут или элемент.  
  
     Здесь *PackageName* — имя файла пакета (PKG), *ModelName* — имя новой модели, *VersionName* — имя версии, а *ServiceName* — полученное на предыдущем шаге имя службы. Убедитесь, что имена модели и версии в точности соответствуют заданным названиям с учетом регистра.  
  
6.  После успешного развертывания пакета отображается сообщение «Операция MDSModelDeploy успешно завершена».  
  
 **Примечания.**  
  
-   Если имя представления подписки в пакете совпадает с именем представления подписки в существующей модели, как создается представление *modelname.subscriptionviewname*. Если это имя уже используется, то представление подписки не создается.  
  
-   Процесс развертывания состоит из четырех шагов.  
  
    1.  Создаются объекты модели.  
  
    2.  Создаются бизнес-правила.  
  
    3.  Создаются представления подписки.  
  
    4.  Производится заполнение основных данных.  
  
-   Если при создании новой или клонированной модели процесс на любом этапе завершается ошибкой, модель удаляется.  
  
     При обновлении в случае неудачного завершения любого из первых трех шагов переход к следующему шагу не производится. Однако откат уже внесенных изменений также не выполняется. Если процесс развертывания завершается неудачей в шаге 4, обновляются те элементы, которые могут обновиться.  
  
## <a name="next-steps"></a>Следующие шаги  
 Определенные пользователем метаданные, атрибуты файлов и разрешения для пользователей и групп не включаются в пакеты развертывания модели. При развертывании модели их нужно обновить вручную. Дополнительные сведения см. в разделе:  
  
-   [Добавить метаданные &#40;службы Master Data Services&#41;](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [Назначение разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Развертывание моделей &#40;службы Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  