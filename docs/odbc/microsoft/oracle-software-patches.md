---
title: Обновления программного обеспечения Oracle | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1fb577e7b08f6ef332ed35f6d275a5f7ce543ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292954"
---
# <a name="oracle-software-patches"></a>Исправления программного обеспечения Oracle
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Исправления для серверных продуктов Oracle и их клиентских компонентов необходимы для правильной работы нескольких продуктов и технологий Майкрософт, включая драйвер Microsoft ODBC для Oracle, поставщик OLE DB для Oracle (Майкрософт), службы IIS (IIS), службы компонентов (или Microsoft Transaction Server, если используется Windows NT) и т. д.  
  
> [!NOTE]  
>  Следующие инструкции могут быть неточными, так как FTP-сайт Oracle может быть изменен.  
  
### <a name="to-download-the-oracle-software-patches"></a>Загрузка обновлений программного обеспечения Oracle  
  
1.  Подключитесь к общедоступному FTP-сайту по адресу oracle-ftp.oracle.com. Идентификатор пользователя — "Anonymous", а пароль — ваш адрес электронной почты.  
  
2.  Перейдите в следующий каталог:/сервер/wgt_tech/сервер/виндовснт.  
  
3.  Чтобы загрузить исправления, наиболее подходящие для Windows 95, Windows 98 и Windows NT или Windows 2000, перейдите в подкаталог для вашей версии Oracle-7,3 или 8,0. Два подкаталога —/73patchsets и/80patchsets.  
  
4.  Чтобы загрузить исправления для сетевой технологии Oracle (SQL * NET или Net8), перейдите в следующий каталог:/Нетворк.  
  
 Доступ к FTP-сайту из веб-браузера может не работать. При возникновении проблем попробуйте использовать "традиционный" FTP-клиент или используйте командную строку DOS.  
  
> [!NOTE]  
>  Поскольку Oracle устраняет ошибки в текущих версиях, а затем перемещает их в более ранние версии с помощью исправлений программного обеспечения, рекомендуется скачать Последнее исправление. Это особенно справедливо для клиентских компонентов сервера Oracle. Если у вас возникли вопросы по установке этих исправлений, обратитесь в службу поддержки Oracle.
