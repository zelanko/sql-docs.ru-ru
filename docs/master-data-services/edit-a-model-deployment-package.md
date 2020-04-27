---
title: Изменение пакета развертывания модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 12cacedc8f195a965b7632760976008ba4b422b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728229"
---
# <a name="edit-a-model-deployment-package"></a>Изменение пакета развертывания модели

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описывается развертывание в MDS выбранных частей модели вместо всей модели. Для этого пакет модели MDS необходимо изменить в редакторе пакетов моделей.  
  
 Мастер редактора пакетов моделей позволяет выбирать в модели отдельные сущности, производные иерархии, представления подписок и бизнес-правила, которые будут включены в пакет MDS и впоследствии развернуты. Части модели, развертывать которые не требуется, вы можете оставить невыбранными. При выборе сущности также автоматически выбираются все зависимые объекты в этой сущности.  
  
 С помощью редактора пакетов моделей можно выбирать части модели в файле пакета, созданном либо средством MDSModelDeploy (оно создает файл пакета, включающий объекты и данные), либо мастером развертывания моделей (он создает файл, включающий только структуру модели). После редактирования модели в пакете используйте средство MDSModelDeploy для развертывания объектов и данных или мастер развертывания моделей для развертывания лишь структуры модели.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Должен существовать пакет модели для изменения. Дополнительные сведения см. в разделах [Развертывание моделей (службы Master Data Services)](../master-data-services/deploying-models-master-data-services.md) и [Создание пакета развертывания модели с помощью мастера](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) или [Создание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
### <a name="to-edit-a-model-deployment-package"></a>Изменения пакета развертывания модели  
  
1.  В проводнике Windows на сервере MDS перейдите в папку *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Запустите ModelPackageEditor.exe.  
  
3.  В мастере редактора пакетов моделей нажмите кнопку **Обзор**, перейдите к папке, в которой содержатся пакеты, выберите пакет и нажмите кнопку **Открыть**. Нажмите кнопку **Далее**.  
  
4.  Выберите сущности, производные иерархии, представления подписок или бизнес-правила, которые необходимо развернуть. Снимите выбор тех из них, которые не требуется развертывать. Нажмите кнопку **Далее**.  
  
5.  Проверьте список выбранных объектов для развертывания. Чтобы изменить его, нажмите кнопку **Назад** и повторите шаг 4.  
  
6.  Нажмите кнопку **Обзор**, перейдите к папке, в которой следует сохранить частичный пакет, и введите имя файла частичного пакета (с расширением .pkg). Нажмите кнопку **Сохранить**.  
  
7.  Нажмите кнопку **Готово**.  
  
## <a name="next-steps"></a>Дальнейшие действия  
  
-   [Развертывание пакета развертывания модели с помощью мастера](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
