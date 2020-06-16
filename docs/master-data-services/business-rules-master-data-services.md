---
title: Бизнес-правила
description: Сведения о бизнес-правилах в Master Data Services, которые могут обновлять данные, отправлять электронную почту или запускать бизнес-процесс или рабочий процесс.
ms.custom: ''
ms.date: 03/18/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f0e8c072ebda3cd314858bfa7aac2885267f1e86
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796447"
---
# <a name="business-rules-master-data-services"></a>Бизнес-правила (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Бизнес-правило в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]— это правило, позволяющее обеспечить качество и точность основных данных. Бизнес-правило можно использовать для автоматического обновления данных, отправки электронной почты или запуска бизнес-процесса или рабочего процесса.  
  
 Примеры бизнес-правил см. в статье [Примеры бизнес-правил (службы Master Data Services) ](../master-data-services/business-rule-examples-master-data-services.md).  
  
## <a name="create-and-publish-business-rules"></a>Создание и публикация бизнес-правил  
 Бизнес-правила представляют собой инструкции **If/Then/Else** , создаваемые в пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Если значение атрибута удовлетворяет указанному условию, выполняется определенное действие. В противном случае выполняется действие Else. Возможны такие действия, как задание значения по умолчанию или изменение значения. Эти действия могут сочетаться с отправкой уведомления по электронной почте.  
  
 Бизнес-правила могут основываться на определенных значениях атрибутов (например, предпринимать действие, если Цвет=Синий) или на изменении значения атрибута (например, предпринимать действие, если значение атрибута «Цвет» изменяется). Дополнительные сведения об отслеживании изменений общего вида см. в разделе [Отслеживание изменений (службы Master Data Services)](../master-data-services/change-tracking-master-data-services.md).  
  
 Для использования бизнес-правил сначала необходимо создать и опубликовать правила, а затем применить опубликованные правила к данным. Правила можно применять к подмножествам данных или ко всем данным в версии путем проверки версии. Версию нельзя зафиксировать, пока все атрибуты не пройдут проверку на соответствие бизнес-правилам.  
  
 Если пользователь пытается добавить значение атрибута, которое не проходит проверку на соответствие бизнес-правилам, это значение все равно можно сохранить. Просмотреть ошибки проверки и исправить их можно в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 При создании пакета развертывания модели в случае необходимости включить бизнес-правила следует включить данные из версии пакета.  
  
 Если в созданном бизнес-правиле используется оператор **OR** , необходимо создать отдельное правило для каждой из условных инструкций, которые можно применить независимо. При необходимости правила можно исключать, что повышает гибкость и упрощает устранение неполадок.  
  
## <a name="how-business-rules-are-applied"></a>Применение бизнес-правил  
 Вы можете установить приоритет, согласно которому следует выполнять правила. Для этого перемещайте бизнес-правила вверх и вниз. Однако перед тем как учесть приоритет, применяются бизнес-правила на основании типа действия, которое предпринимает правило. Порядок выглядит следующим образом.  
  
1.  **Значение по умолчанию**  
  
2.  **Изменить значение**  
  
3.  **Проверка**  
  
4.  **Внешнее действие**  
  
5.  **Пользовательский сценарий действия**  
  
 В рамках этих групп действия применяются в порядке, определенном их приоритетом, — от самого низкого до самого высокого. Так, например, четыре отдельных правила могут содержать действия **Значение по умолчанию** . Выполняемое первым действие **Значение по умолчанию** зависит от приоритета, определенного в веб-интерфейсе.  
  
 Другие важные замечания о применении правил.  
  
-   Если бизнес-правило исключено или не опубликовано с состоянием **Активно**, оно по-прежнему доступно, но не используется в процессе применения бизнес-правил.  
  
-   Бизнес-правила применяются к значениям атрибутов для всех конечных элементов или всех консолидированных элементов, но не для тех и других сразу.  
  
-   Бизнес-правила могут применяться к любым версиям модели, то есть к **Открытым** или **Заблокированным**.  
  
-   Изменения данных при применении бизнес-правил не регистрируются как транзакции.  
  
-   Бизнес-правило не может содержать более одного действия **запуска рабочего процесса** .  
  
## <a name="system-settings"></a>Системные настройки  
 В программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] имеется два параметра, которые влияют на бизнес-правила. Эти параметры можно настроить в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или непосредственно в таблице системных настроек. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание и публикация бизнес-правила.|[Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Добавление нескольких условий к бизнес-правилу.|[Добавление нескольких условий к бизнес-правилу (службы Master Data Services)](../master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|Создание бизнес-правила, которое требует заполнения атрибутов.|[Запрос значений атрибута (службы Master Data Services)](../master-data-services/require-attribute-values-master-data-services.md)|  
|Создание бизнес-правила, которое запускает действие при изменении значений атрибутов.|[Инициирование действия на основе значения атрибута (службы Master Data Services)](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|Создание бизнес-правила для использования пользовательского сценария как условия|[Расширение бизнес-правил (службы Master Data Services)](../master-data-services/business-rules-extension-master-data-services.md)|  
|Создание бизнес-правила для использования пользовательского сценария как действия|[Расширение бизнес-правил (службы Master Data Services)](../master-data-services/business-rules-extension-master-data-services.md)|  
|Изменение имени существующего бизнес-правила.|[Изменение имени бизнес-правила (службы Master Data Services)](../master-data-services/change-a-business-rule-name-master-data-services.md)|  
|Настройка [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для отправки уведомлений при применении бизнес-правил.|[Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|Применение бизнес-правил к определенным элементам.|[Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Исключите бизнес-правило, чтобы оно не использовалось.|[Исключение бизнес-правила (службы Master Data Services)](../master-data-services/exclude-a-business-rule-master-data-services.md)|  
|Удаление существующего бизнес-правила.|[Удаление бизнес-правила (службы Master Data Services)](../master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)  
  
-   [Проверка (службы Master Data Services)](../master-data-services/validation-master-data-services.md)  
  
-   [Отслеживание изменений (службы Master Data Services)](../master-data-services/change-tracking-master-data-services.md)  
  
  
