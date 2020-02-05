---
title: Свойства браузера SQL Server (вкладка «Вход в систему»)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e1457374ca9e7ba7a0504e7c025333d3bcd48c20
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307099"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Свойства браузера SQL Server (вкладка «Вход в систему»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Программа браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в качестве службы на сервере. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установленных на компьютере.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Браузер прослушивает UDP-порт и принимает запросы без проверки подлинности с использованием протокола разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP).  
  
 Изменение пароля учетной записи вступает в силу немедленно, без перезапуска службы.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Запустите службу « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , браузер» в контексте безопасности локальной системной учетной записи. По возможности используйте учетную запись с небольшим набором прав.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись, использующую аутентификацию Windows. Для служб рекомендуется использовать доменную учетную запись с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Обзор**  
 Выберите пользователя или встроенного субъекта безопасности.  
  
> [!IMPORTANT]  
>  Используйте учетную запись с минимальными правами. Дополнительные сведения о разрешениях, необходимых для службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе "Безопасность" статьи [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 **Пароль**  
 Введите пароль субъекта безопасности.  
  
 **Подтверждение пароля**  
 Подтвердите пароль субъекта безопасности.  
  
 **Состояние службы**  
 Указывает, была ли служба запущена, остановлена или отключена. **…** указывает, что ожидается изменение состояния.  
  
 **Начало**  
 Запустить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Остановить**  
 Остановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Приостановить**  
 Приостановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Возобновить**  
 Возобновить работу приостановленной службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
