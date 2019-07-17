---
title: Исправления программного обеспечения Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fce38aabddfc3891314940d4b7cb21f02965c083
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100768"
---
# <a name="oracle-software-patches"></a>Исправления программного обеспечения Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Исправления для серверных продуктов Oracle и ее клиентский компонент необходимы для правильной работы нескольких продуктов и технологий Microsoft, включая драйвер Microsoft ODBC для Oracle, поставщик Microsoft OLE DB для Oracle, Internet Information Службы IIS, службы компонентов (или Microsoft Transaction Server, если вы используете Windows NT), и т. д.  
  
> [!NOTE]  
>  Приведенные ниже инструкции не может быть вполне точной, поскольку сайт Oracle FTP может быть изменена.  
  
### <a name="to-download-the-oracle-software-patches"></a>Для загрузки исправления программного обеспечения Oracle  
  
1.  Подключитесь к общедоступный сайт FTP в oracle ftp.oracle.com. Идентификатор пользователя — «anonymous», а пароль — ваш адрес электронной почты.  
  
2.  Перейдите к следующему каталогу: /server/wgt_tech/server/windowsNT.  
  
3.  Чтобы загрузить наиболее важные исправления для Windows 95, Windows 98 и Windows NT и Windows 2000, перейдите к подкаталогу для вашей версии Oracle - 7.3 или 8.0. Две подпапки, /73patchsets и /80patchsets.  
  
4.  Для скачивания исправлений для технологии Oracle в сети, либо SQL * Net или Net8, перейдите к следующему каталогу: / сети.  
  
 Доступ к FTP-сайта из веб-браузере может не работать. Если вы столкнулись с проблемами, попробуйте использовать «традиционные» FTP-клиента или с помощью командной строки DOS.  
  
> [!NOTE]  
>  Так как Oracle, исправления ошибок в текущей версии и затем retrofits их на более ранние версии, с помощью исправления программного обеспечения, рекомендуется загрузить последнюю исправление. Это особенно верно для Oracle Server клиентские компоненты. Если у вас есть вопросы об установке эти исправления, обратитесь в службу поддержки Oracle.
