---
title: Патчи программного обеспечения Oracle (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292954"
---
# <a name="oracle-software-patches"></a>Исправления программного обеспечения Oracle
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Патчи для серверных продуктов Oracle и его клиентского компонента необходимы для нормального функционирования нескольких продуктов и технологий Microsoft, включая Microsoft ODBC Driver для Oracle, Microsoft OLE DB Provider for Oracle, Internet Information Services (IIS), Компонентные службы (или Microsoft Transaction Server, если вы используете Windows NT) и так далее.  
  
> [!NOTE]  
>  Следующие инструкции могут быть не совсем точными, поскольку сайт Oracle FTP может быть изменен.  
  
### <a name="to-download-the-oracle-software-patches"></a>Для загрузки патчей программного обеспечения Oracle  
  
1.  Подключайтесь к общедоступному сайту FTP по адресу oracle-ftp.oracle.com. Идентификатор пользователя является "анонимным", а пароль - вашим адресом электронной почты.  
  
2.  Перейдите к следующему каталогу: /сервер/wgt_tech/сервер/windowsNT.  
  
3.  Чтобы загрузить патчи, наиболее актуальные для Windows 95, Windows 98 и Windows NT/Windows 2000, перейдите в субдиректор для вашей версии Oracle - 7.3 или 8.0. Двумя субдиректорами являются /73patchsets и /80patchsets.  
  
4.  Чтобы загрузить патчи для сетевой технологии Oracle, как s'L-Net, так и Net8, перейдите к следующему каталогу: /network.  
  
 Доступ к этому веб-сайту FTP из вашего веб-браузера может не работать. Если возникли проблемы, попробуйте использовать "традиционный" клиент FTP или использовать запрос команды DOS.  
  
> [!NOTE]  
>  Поскольку Oracle исправляет ошибки в текущих версиях, а затем переоборудует их в более ранние версии с помощью программных патчей, рекомендуется загрузить последний доступный патч. Это особенно верно для компонентов Oracle Server Client. Если у вас возникли вопросы об установке этих патчей, обратитесь в службу поддержки Oracle.
