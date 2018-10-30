---
title: Отправка документов в библиотеку SharePoint (службы Reporting Services в режиме интеграции с SharePoint) | Документы Майкрософт
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9662a3e69b7d870b7f376f7a0c699db75584ad62
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021088"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a>Отправка документов в библиотеку SharePoint (службы Reporting Services в режиме интеграции с SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Можно передать определения отчета и модели отчета в библиотеку SharePoint. При передаче элемента сервера отчетов необходимо выбрать библиотеку или папку внутри библиотеки. Невозможно передать элемент сервера отчетов в список или на страницу.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

 Передача RDS-файла источника данных невозможна. Однако можно опубликовать RDS-файлы с помощью средства проектирования, такого как конструктор отчетов, для включения в библиотеку SharePoint. Во время публикации новый RSDS-файл создается из исходного RDS-файла в решении. Можно также создать новый RSDS-файл в библиотеке SharePoint, а потом установить свойства соединения с источником данных в передаваемых отчетах и моделях, чтобы использовать новое соединение.  
  
> [!NOTE]  
>  Сервер отчетов необходимо настроить для работы в режиме интеграции с SharePoint, а экземпляр продукта SharePoint должен иметь надстройку служб Reporting Services, которая предоставляет программные файлы для хранения и доступа к элементам сервера отчетов с сайта SharePoint.  
  
 Чтобы передать документ в библиотеку, необходимо обладать разрешением на добавление элементов на уровне веб-сайта. При использовании настроек безопасности по умолчанию это разрешение предоставляется членам группы **Владельцы** , которые обладают разрешением уровня «Полный контроль» и группе **Члены** , которая обладает разрешением уровня «Участие».  
  
## <a name="add-a-report-definition-or-report-model-to-a-library"></a>Добавление определения отчета или модели отчета в библиотеку
  
1.  Откройте библиотеку или папку в библиотеке. Если библиотека еще не открыта, щелкните ее имя на панели «Быстрый запуск». Если имя библиотеки не отображается, щелкните **Просмотреть содержимое всего сайта**и выберите имя библиотеки.  
  
2.  В меню **Передача** выберите команду **Передать документ**.  
  
3.  Чтобы передать один отчет или файл модели отчета, выберите RDL-файл определения отчета или SMDL-файл модели отчета и нажмите кнопку **ОК**.  
  
     Если определение отчета использует файл общего источника данных (RSDS) для хранения сведений о соединении с внешним источником данных, можно одновременно передать и RDL-файл, и RSDS-файл. Для этого выберите **Передать несколько документов**, укажите оба файла и нажмите кнопку **ОК**.  
  
 При передаче отчета, который содержит ссылки на общие источники данных, модели отчетов или вложенные отчеты, ссылки будут потеряны при передаче файлов. Дополнительные сведения о сбросе ссылок см. в разделе [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](https://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).  
  
 При передаче отчет выполняется по запросу при его открытии, при этом из источника данных извлекаются активные данные. Можно настроить отчет на получение данных по расписанию или на использование кэшированных данных. Дополнительные сведения см. в разделе [Установка параметров обработки (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
 Отчет может содержать параметры, поэтому пользователи могут фильтровать данные. Можно настроить параметры на использование конкретных значений или изменить способ их представления для пользователя. Дополнительные сведения см. в разделе [Настройка параметров опубликованного отчета (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>См. также раздел

 [опубликовать отчет в библиотеке SharePoint](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [опубликовать общий источник данных в библиотеке SharePoint](../../reporting-services/reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
