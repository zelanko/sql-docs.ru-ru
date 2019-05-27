---
title: Редактор задачи «FTP» (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ad2605902cb523c0147888e4aedee0df3c9f936e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058431"
---
# <a name="ftp-task-editor-general-page"></a>Редактор задачи «FTP» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «FTP»** для задания диспетчера FTP-соединений, выполняющего соединение с FTP-сервером, с которым задача обменивается данными. Также здесь можно указать имя и описание задачи «FTP».  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](control-flow/ftp-task.md).  
  
## <a name="options"></a>Параметры  
 **FtpConnection**  
 Выберите существующий диспетчер подключений FTP или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
> [!IMPORTANT]  
>  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 **См. также**: [Диспетчер FTP-сеансов](connection-manager/ftp-connection-manager.md), [Редактор диспетчера FTP-сеансов](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **StopOnFailure**  
 Укажите, следует ли завершить задачу «FTP» в случае ошибки операции с FTP.  
  
 **Название**  
 Задайте уникальное имя задачи «FTP». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи «FTP».  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "FTP" (страница "Передача файлов")](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
