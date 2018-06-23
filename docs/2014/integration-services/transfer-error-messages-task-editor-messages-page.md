---
title: Редактор передача сообщений об задачи (страница «сообщения») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 833f092574c85ab83f6a384b77e7f8c99c91b2c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101562"
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
 Нажмите кнопку обзора, обозначенную многоточием **(...)** , чтобы выбрать сообщения об ошибках для копирования.  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
 **ErrorMessageLanguagesList**  
 Нажмите кнопку обзора, обозначенную многоточием **(...)** , чтобы выбрать языки, для которых должны быть скопированы на целевой сервер пользовательские сообщения об ошибках. Прежде чем можно будет передать на целевой сервер версии сообщения на других языках, на нем должна существовать англоязычная версия сообщения (кодовая страница 1033, us_english).  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задач сообщений об ошибках передачи &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Диспетчер соединений SMO](connection-manager/smo-connection-manager.md)   
 [Редактор задач сообщений об ошибках передачи &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Диспетчер подключений управляющих объектов SQL Server](connection-manager/smo-connection-manager.md)  
  
  