---
title: Редактор диспетчера HTTP-сеансов (страница «прокси-сервер») | Документы Microsoft
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
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 726133083a8cd0f5be2bb6d20740c80c79c3fe75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194527"
---
# <a name="http-connection-manager-editor-proxy-page"></a>Редактор диспетчера HTTP-соединений (страница «Прокси-сервер»)
  Используйте вкладку **Прокси-сервер** диалогового окна **Редактор диспетчера HTTP-соединений** , чтобы настроить диспетчер HTTP-соединений для работы с прокси-сервером. HTTP-соединение позволяет пакету получить доступ к веб-серверу через протокол HTTP, чтобы передавать или принимать файлы.  
  
 Дополнительные сведения о диспетчере HTTP-соединений см. в разделе [HTTP Connection Manager](connection-manager/http-connection-manager.md). Дополнительные сведения о распространенном сценарии использования диспетчера HTTP-соединений см. в разделе [Web Service Task](control-flow/web-service-task.md).  
  
## <a name="options"></a>Параметры  
 **Использовать прокси-сервер**  
 Укажите, должен ли диспетчер HTTP-сеансов подключаться через прокси-сервер.  
  
 **URL-адрес прокси-сервера**  
 Введите URL-адрес прокси-сервера.  
  
 **Не использовать прокси-сервер при локальном подключении**  
 Укажите, должен ли диспетчер HTTP-соединений исключать прокси-сервер для локальных адресов.  
  
 **Использовать учетные данные**  
 Укажите, должен ли диспетчер HTTP-соединений использовать учетные данные для прокси-сервера.  
  
 **Имя пользователя**  
 Если диспетчер HTTP-соединений использует учетные данные, необходимо указать имя пользователя, пароль и домен.  
  
 **Пароль**  
 Если диспетчер HTTP-соединений использует учетные данные, необходимо указать имя пользователя, пароль и домен.  
  
 **Домен**  
 Если диспетчер HTTP-соединений использует учетные данные, необходимо указать имя пользователя, пароль и домен.  
  
 **Список адресов, не требующих прокси-сервера**  
 Список адресов, для которых прокси-сервер использоваться не должен.  
  
 **Добавить**  
 Введите адрес, для которого прокси-сервер использоваться не должен.  
  
 **Удалить**  
 Выберите адрес и затем удалите его, нажав кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор диспетчера HTTP-соединений &#40;страница сервера&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
  