---
title: Служба Windows сервера отчетов (MSSQLServer) 107 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad8ff3e2a6d87c680c34ae3f2926799e28c3268e
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59946596"
---
# <a name="report-server-windows-service-mssqlserver-107"></a>Служба Windows сервера отчетов (MSSQLServer) 107
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|107|  
|Источник события|Служба Windows сервера отчетов|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Служба Windows сервера отчетов (MSSQLSERVER) не может соединиться с базой данных сервера отчетов.|  
  
## <a name="explanation"></a>Объяснение  
 Службе сервера отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается соединиться с базой данных сервера отчетов. Такая ошибка возникает при перезапуске службы, если не удается установить соединение с базой данных сервера отчетов. Эта ошибка возникает при следующих условиях.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] — не была запущена служба в момент запуска службы сервера отчетов.  
  
-   Не удалось установить соединение со службой компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , так как не включено использование удаленных соединений или протокола TCP/IP.  
  
-   База данных сервера отчетов настроена неправильно.  
  
-   Учетная запись службы настроена неправильно или не имеет разрешений для доступа к базе данных сервера отчетов. Это может произойти в том случае, если настройка учетной записи или базы данных сервера отчетов производилась не через программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Если служба компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] еще не запущена, то запустите ее и убедитесь, что включены удаленные соединения для протокола TCP/IP.  
  
 Производите настройку базы данных сервера отчетов и учетной записи службы при помощи программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Запуск и остановка службы сервера отчетов](../report-server/start-and-stop-the-report-server-service.md)  
  
  
