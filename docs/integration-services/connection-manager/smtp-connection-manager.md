---
title: Диспетчер подключений SMTP | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.smtpconnection.f1
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f36ab7571008b73d90cc337e3fe7f5e5fa8523
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087434"
---
# <a name="smtp-connection-manager"></a>Диспетчер соединений SMTP

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диспетчер соединений SMTP предоставляет пакету возможность подключения к серверу SMTP (Simple Mail Transfer Protocol). Задача "Отправка почты" из состава служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует диспетчер соединений SMTP.  
  
 При использовании Microsoft Exchange в качестве SMTP-сервера, возможно, появится необходимость установить конфигурацию диспетчера соединений SMTP для использования проверки подлинности Windows. Серверы Exchange можно конфигурировать так, чтобы они не разрешали SMTP-сеансы, не прошедшие проверку подлинности.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Настройка диспетчера соединений SMTP  
 При добавлении к пакету диспетчера подключений SMTP [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который будет разрешен в соединение SMTP во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **SMTP**.  
  
 Произвести настройку конфигурации диспетчера соединений SMTP можно следующими способами:  
  
-   Указать строку соединения.  
  
-   Укажите имя SMTP-сервера.  
  
-   Выберите метод проверки подлинности.  
  
    > [!IMPORTANT]  
    >  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
-   Укажите, будет ли отправка сообщений электронной почты шифроваться с использованием протокола TLS (прежнее название — SSL).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера SMTP-сеансов](../../integration-services/connection-manager/smtp-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="smtp-connection-manager-editor"></a>редактор диспетчера SMTP-сеансов
  Используйте диалоговое окно **Редактор диспетчера SMTP-сеансов** для задания SMTP-сервера.  
  
 Дополнительные сведения о диспетчере SMTP-соединений см. в разделе [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
### <a name="options"></a>Параметры  
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
>  При использовании Microsoft Exchange в качестве SMTP-сервера, возможно, потребуется присвоить параметру **Использовать проверку подлинности Windows** значение **True**. Серверы Exchange можно настроить так, чтобы они запрещали использовать соединения SMTP, не прошедшие проверку подлинности.  
  
 **Включить протокол SSL**  
 Выберите, чтобы отправляемые сообщения электронной почты шифровались по протоколу SSL или TLS.  
  
