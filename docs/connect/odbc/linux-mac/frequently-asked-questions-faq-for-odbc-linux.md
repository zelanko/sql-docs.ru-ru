---
title: Часто задаваемые вопросы об ODBC в Linux и macOS
description: Найдите ответы на часто задаваемые вопросы о Microsoft ODBC Driver for SQL Server на Linux и macOS.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700c89b520cdaa33a60f1adabe69c669388bcccb
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82886459"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Часто задаваемые вопросы об ODBC в Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Ниже приведены ответы на вопросы о драйвере ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS.
  
## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

**Как работают с драйвером существующие приложения ODBC в Linux и macOS?**  
Вы должны быть в состоянии компилировать и запускать приложения ODBC, которые компилировались и запускались в Linux или macOS с использованием других драйверов. 
  
**Какие функции [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] поддерживает эта версия драйвера?**

Драйвер ODBC для Linux и macOS поддерживает все функции сервера в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], за исключением LocalDB. Дополнительные сведения о поддерживаемых функциях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в статье [Programming Guidelines](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Поддерживает ли драйвер проверку подлинности Kerberos?**  
Да. При наличии существующей установки среды Kerberos вы сможете подключиться к серверам, используя имя DSN `Trusted_Connection=Yes` или строку подключения. Дополнительные сведения см. в статье [Использование встроенной проверки подлинности](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Какую кодировку Юникода должно использовать приложение?**  
UTF-8 для данных SQL_CHAR и UTF-16 для данных SQL_WCHAR. В зависимости от языкового стандарта и версии драйвера, могут поддерживаться данные и в некоторых других кодировках, кроме UTF-8. Более подробную информацию см. в статье [Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md).

**Существуют ли примеры ODBC, которые я могу скачать и запустить с помощью драйвера, чтобы поэкспериментировать с ним или оценить его?**

Пример см. в статье [Использование существующих примеров MSDN C++ ODBC для драйвера ODBC в Linux](/archive/blogs/sqlblog/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver) . Это также применимо к драйверу ODBC для macOS.

**Имеет ли драйвер ODBC для Linux открытый исходный код?**

Нет, драйвер ODBC для Linux не является продуктом с открытым исходным кодом.  

## <a name="see-also"></a>См. также:

- [Установка Microsoft ODBC Driver for SQL Server в Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Установка Microsoft ODBC Driver for SQL Server в macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
