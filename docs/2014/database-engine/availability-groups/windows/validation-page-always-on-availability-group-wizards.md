---
title: Страница "Проверка" (мастера групп доступности AlwaysOn) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6cf16c8afb363a1b7727b6da3a5f75bf966ab0d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62812995"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a>Страница проверки (мастера групп доступности AlwaysOn)
  В этом разделе описываются параметры, приведенные на странице **Проверка** . Эта тема относится к [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]и [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Используйте эту страницу для проверки поддержки средой всех вариантов конфигурации, выбранных на предыдущей странице мастера.  
  
##  <a name="PageOptions"></a>Параметры страницы проверки  
 **Результаты проверки группы доступности.**  
 В этой сетке отображаются результаты каждого завершенного этапа проверки. Сетка содержит следующие столбцы.  
  
 **Название**  
 Отображает фразу, которая описывает конкретный шаг.  
  
 **Результат**  
 Отображает один из следующих текстов гиперссылки. Дополнительные сведения данного шага проверки можно просмотреть, щелкнув гиперссылку.  
  
|Результат|Description|  
|------------|-----------------|  
|**Ошибка**|Указывает, что шаг проверки выполнен неудачно. Щелкните ссылку, чтобы просмотреть сообщение об ошибке.|  
|**Пропущено**|Указывает, что шаг проверки был пропущен, поскольку он не был отмечен в параметрах как необходимый. Щелкните ссылку для просмотра причины, по которой шаг был пропущен.|  
|**Успех**|Указывает, что шаг проверки завершен удачно.|  
|**Предупреждение**|Указывает на наличие потенциальной проблемы с конфигурацией группы доступности.  Щелкните ссылку, чтобы просмотреть предупреждение.|  
  
 **Повторно запустить проверку**  
 Щелкните, чтобы повторить шаги проверки, если в ответ на выявленную ошибку были внесены изменения без использования средств мастера.  
  

  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Используйте диалоговое окно Создание группы доступности &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления базы данных в группу доступности &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
