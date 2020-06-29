---
title: Редактор диспетчера SMTP-соединений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b303c15dbbad37a48b41ec73ed2c4baa461d5b13
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421331"
---
# <a name="smtp-connection-manager-editor"></a>редактор диспетчера SMTP-сеансов
  Используйте диалоговое окно **Редактор диспетчера SMTP-сеансов** для задания SMTP-сервера.  
  
 Дополнительные сведения о диспетчере SMTP-соединений см. в разделе [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Задает уникальное имя диспетчера соединений.  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **SMTP-сервер**  
 Позволяет задать имя сервера SMTP.  
  
 **Использовать проверку подлинности Windows**  
 Выберите для отправки почты с помощью SMTP-сервера, который использует проверку подлинности Windows для доступа к серверу.  
  
> [!IMPORTANT]  
>  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
> [!NOTE]  
>  При использовании Microsoft Exchange в качестве SMTP-сервера может потребоваться задать для параметра **использовать проверку подлинности Windows** значение `True` . Серверы Exchange можно настроить так, чтобы они запрещали использовать соединения SMTP, не прошедшие проверку подлинности.  
  
 **Включить протокол SSL**  
 Выберите, чтобы отправляемые почтовые сообщения шифровались по протоколу SSL.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
