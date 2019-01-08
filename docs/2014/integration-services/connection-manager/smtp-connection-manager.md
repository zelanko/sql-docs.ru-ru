---
title: Диспетчер подключений SMTP | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5233515a94603520a2cbfa03ab497f3246ed06ec
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790717"
---
# <a name="smtp-connection-manager"></a>Диспетчер соединений SMTP
  Диспетчер соединений SMTP предоставляет пакету возможность подключения к серверу SMTP (Simple Mail Transfer Protocol). Задача «Отправка почты» из состава служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует диспетчер соединений SMTP.  
  
 При использовании Microsoft Exchange в качестве SMTP-сервера, возможно, появится необходимость установить конфигурацию диспетчера соединений SMTP для использования проверки подлинности Windows. Серверы Exchange можно конфигурировать так, чтобы они не разрешали SMTP-сеансы, не прошедшие проверку подлинности.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Настройка диспетчера соединений SMTP  
 При добавлении к пакету диспетчера соединений SMTP [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который будет разрешен в соединение SMTP во время выполнения, устанавливает свойства диспетчера соединений и добавляет его к коллекции `Connections` пакета. Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `SMTP`.  
  
 Произвести настройку конфигурации диспетчера соединений SMTP можно следующими способами:  
  
-   Указать строку соединения.  
  
-   Укажите имя SMTP-сервера.  
  
-   Выберите метод проверки подлинности.  
  
    > [!IMPORTANT]  
    >  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
-   Укажите, будет ли отправка сообщений электронной почты шифроваться с использованием протокола SSL.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера SMTP-сеансов](../smtp-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
