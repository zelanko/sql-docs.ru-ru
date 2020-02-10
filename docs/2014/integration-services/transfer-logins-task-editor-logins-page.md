---
title: Редактор задачи «Перемещение имен входа» (страница «имена входа») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ae8ebf56e4ae7c4fce3566cb7688d203b8ceb318
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054925"
---
# <a name="transfer-logins-task-editor-logins-page"></a>Редактор задачи «Передача имен входа» (страница «Имена входа»)
  Страница **Имена входа** диалогового окна **Редактор задачи «Передача имен входа»** используется для задания свойств для копирования одного или более имен входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в другой. Дополнительные сведения об этой задаче см. в разделе [Transfer Logins Task](control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  При выполнении задачи «Передача имен входа» имена создаются на целевом сервере со случайными паролями, и эти пароли отключаются. Для использования этих имен входа элемент предопределенной роли сервера **sysadmin** должен изменить пароли и затем включить их. Не удается передать имя входа **SA** .  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с исходным сервером.  
  
 **DestinationConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с целевым сервером.  
  
 **LoginsToTransfer**  
 Выберите имена входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для копирования их с исходного сервера на целевой. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**AllLogins**|Все имена входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на исходном сервере будут скопированы на целевой сервер.|  
|**Значение selectedlogins**|На целевой сервер будут скопированы только имена входа, заданные списком **LoginsList** .|  
|**AllLoginsFromSelectedDatabases**|Все имена входа из баз данных, заданных списком **DatabasesList** , будут скопированы на целевой сервер.|  
  
 **LoginsList**  
 Определяет имена входа на исходном сервере для копирования на целевой сервер. Этот параметр доступен только в том случае, если значение **SelectedLogins** выбрано для **LoginsToTransfer**.  
  
 **DatabasesList**  
 Определяет базы данных на исходном сервере, которые содержат имена входа для копирования на целевой сервер. Этот параметр доступен только в том случае, если значение **AllLoginsFromSelectedDatabases** выбрано для **LoginsToTransfer**.  
  
 **Перечислении ifobjectexists**  
 Определяет то, как задача должна обрабатывать имена входа с тем же названием, что и у существующих на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**FailTask**|Задача не выполняется, если такое же имя входа уже существует на целевом сервере.|  
|**Перезаписать**|Задача перезаписывает имя входа на целевом сервере.|  
|**Сразу**|Задача пропускает обработку имени входа, если такое же имя входа уже существует на целевом сервере.|  
  
 **CopySids**  
 Определяет, будут ли скопированы на целевой сервер идентификаторы безопасности, связанные с именами входа. **Параметр CopySids** должно иметь значение **true** , если задача «Перемещение имен входа» используется вместе с задачей «перенос базы данных». В противном случае скопированные имена входа не будут распознаны переданными базами данных.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "Перемещение имен входа" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Диспетчер соединений SMO](connection-manager/smo-connection-manager.md)   
 [Надежные пароли](../relational-databases/security/strong-passwords.md)   
 [Вопросы безопасности при установке SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
