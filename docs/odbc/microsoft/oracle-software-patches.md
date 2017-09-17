---
title: "Обновления программного обеспечения Oracle | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bab4a7bed2fdc63224fd7a2f86757d11375f2cd2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="oracle-software-patches"></a>Обновления программного обеспечения Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Исправления для клиента компонент и продуктах Oracle server требуются для правильной работы нескольких продуктов и технологий, включая драйвер Microsoft ODBC для Oracle и поставщик Microsoft OLE DB для Oracle, Internet Information корпорации Майкрософт Службы IIS, службы компонентов (или Microsoft Transaction Server, если вы используете Windows NT), и т. д.  
  
> [!NOTE]  
>  Приведенные ниже инструкции могут быть не вполне точной так как сайт Oracle FTP может быть изменено.  
  
### <a name="to-download-the-oracle-software-patches"></a>Чтобы загрузить обновления программного обеспечения Oracle  
  
1.  Подключиться к общей FTP-сайта в oracle ftp.oracle.com. Идентификатор пользователя «anonymous», а пароль — адрес электронной почты.  
  
2.  Перейдите в следующий каталог: /server/wgt_tech/server/windowsNT.  
  
3.  Чтобы загрузить наиболее важные обновления для Windows 95, Windows 98 и Windows NT и Windows 2000, перейдите в подкаталог для вашей версии Oracle — 7.3 или 8.0. Две вложенные папки: /73patchsets и /80patchsets.  
  
4.  Для загрузки исправлений для технологии Oracle в сети, либо SQL * Net или Net8, перейдите в следующий каталог: / сети.  
  
 Доступ к FTP-сайта из веб-браузере может не работать. Если возникли проблемы, попробуйте использовать «традиционные» FTP-клиента или используйте командную строку DOS.  
  
> [!NOTE]  
>  Поскольку Oracle устраняет ошибки в текущей версии и затем retrofits их на более ранние версии, с помощью обновления программного обеспечения, рекомендуется загрузить последние исправление. Это особенно верно для компонентов сервера клиента Oracle. Если у вас есть вопросы об установке этих исправлений, обратитесь в службу поддержки Oracle.
