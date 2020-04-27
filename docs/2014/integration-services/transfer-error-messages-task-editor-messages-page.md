---
title: Редактор задачи «перенос сообщений об ошибках» (страница «сообщения») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f753aaddbd2647b1d8874b0d34db415f75aa99b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055038"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Редактор задачи «Передача сообщений об ошибках» (страница «Сообщения»)
  Используйте страницу **Сообщения** диалогового окна **Редактор задачи "Передача сообщений об ошибках"** , чтобы указать свойства копирования одного или более определенных пользователем сообщений об ошибках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в другой. Дополнительные сведения об этой задаче см. в разделе [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с исходным сервером.  
  
 **DestinationConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с целевым сервером.  
  
 **IfObjectExists**  
 Выберите, следует ли при выполнении задачи перезаписать существующие пользовательские сообщения об ошибках, оставить их без изменения или зарегистрировать сбой в случае, если сообщения об ошибках с тем же именем уже существуют на целевом сервере.  
  
 **TransferAllErrorMessages**  
 Выберите, следует ли при выполнении задачи копировать все или только указанные пользовательские сообщения с исходного сервера на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Условия**|Копировать все пользовательские сообщения.|  
|**IsFalse**|Копировать только указанные пользовательские сообщения.|  
  
 **ErrorMessagesList**  
 Нажмите кнопку обзора **(...)** , чтобы выбрать сообщения об ошибках для копирования.  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
 **ErrorMessageLanguagesList**  
 Нажмите кнопку обзора **(...)** , чтобы выбрать языки, для которых необходимо скопировать определяемые пользователем сообщения об ошибках на целевой сервер. Прежде чем можно будет передать на целевой сервер версии сообщения на других языках, на нем должна существовать англоязычная версия сообщения (кодовая страница 1033, us_english).  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "перенаправление сообщений об ошибках" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Диспетчер соединений SMO](connection-manager/smo-connection-manager.md)   
 [Редактор задачи "перенаправление сообщений об ошибках" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [SMO, диспетчер соединений](connection-manager/smo-connection-manager.md)  
  
  
