---
title: "Часто задаваемые вопросы и для ODBC Linux и macOS | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aa835ce2bb9e35191d9c3056dad2f208445c361a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Часто задаваемые вопросы и для ODBC Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Ниже приведены ответы на вопросы о драйвере ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux и macOS.
  
## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

**Как существующие приложения ODBC в Linux или macOS работают с драйвером**  
Вы сможете компилировать и запускать приложения ODBC, которые вы компиляции и под управлением Linux или macOS с использованием других драйверов. 
  
**Какие функции [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] эта версия поддержка драйвера?**

Драйвер ODBC для Linux и macOS поддерживает все функции сервера в [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] за исключением LocalDB. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддерживаемые функции в разделе [рекомендации по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Поддерживает ли драйвер проверку подлинности Kerberos?**  
Да. Если у вас есть существующая среда Настройка Kerberos, можно подключаться к серверам с помощью `Trusted_Connection=Yes` DSN или строке параметр соединения. Дополнительные сведения см. в разделе [с помощью встроенной проверки подлинности](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Какую кодировку Юникод должно использовать приложение?**  
UTF-8 для данных SQL_CHAR и UTF-16 для данных SQL_WCHAR.  

**Существуют ли примеры ODBC, которые можно загрузить и запустить с помощью драйвера, чтобы поэкспериментировать с или оценить его?**

Пример см. в статье [Использование существующих примеров MSDN C++ ODBC для драйвера ODBC в Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Это также применимо к драйверу ODBC macOS. 

**Имеет ли драйвер ODBC для Linux или macOS с открытым кодом?**

Нет, драйверы ODBC в Linux и macOS не продукт с открытым кодом.  

## <a name="see-also"></a>См. также:
[Установка Microsoft ODBC Driver for SQL Server для Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

