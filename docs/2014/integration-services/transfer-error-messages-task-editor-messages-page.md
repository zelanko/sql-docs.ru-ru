---
title: Редактор передача сообщений об задачи (страница "сообщения") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d83edf8ee65b638525c0ddd5ee994a26cfcfbd70
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52545800"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Редактор задачи «Передача сообщений об ошибках» (страница «Сообщения»)
  Используйте страницу **Сообщения** диалогового окна **Редактор задачи "Передача сообщений об ошибках"**, чтобы указать свойства копирования одного или более определенных пользователем сообщений об ошибках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в другой. Дополнительные сведения об этой задаче см. в разделе [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к целевому серверу.  
  
 **IfObjectExists**  
 Выберите, следует ли при выполнении задачи перезаписать существующие пользовательские сообщения об ошибках, оставить их без изменения или зарегистрировать сбой в случае, если сообщения об ошибках с тем же именем уже существуют на целевом сервере.  
  
 **TransferAllErrorMessages**  
 Выберите, следует ли при выполнении задачи копировать все или только указанные пользовательские сообщения с исходного сервера на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Копировать все пользовательские сообщения.|  
|**False**|Копировать только указанные пользовательские сообщения.|  
  
 **ErrorMessagesList**  
 Нажмите кнопку обзора, обозначенную многоточием **(...)**, чтобы выбрать сообщения об ошибках для копирования.  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
 **ErrorMessageLanguagesList**  
 Нажмите кнопку обзора, обозначенную многоточием **(...)**, чтобы выбрать языки, для которых должны быть скопированы на целевой сервер пользовательские сообщения об ошибках. Прежде чем можно будет передать на целевой сервер версии сообщения на других языках, на нем должна существовать англоязычная версия сообщения (кодовая страница 1033, us_english).  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача сообщений об ошибках" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Диспетчер соединений SMO](connection-manager/smo-connection-manager.md)   
 [Редактор задачи "Передача сообщений об ошибках" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Диспетчер подключений управляющих объектов SQL Server](connection-manager/smo-connection-manager.md)  
  
  
