---
title: Развертывание драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dc9f01dd72d96a50df220c84827bd7afb826168c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-the-jdbc-driver"></a>Развертывание драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При развертывании приложения, зависящего от [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], драйвер JDBC необходимо повторно распространить вместе с приложением. В отличие от Windows компоненты доступа к данным (Windows DAC), который является компонентом операционной системы Windows, драйвер JDBC считается компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
 Для развертывания драйвера JDBC в приложении используются два подхода. При использовании одного файлы драйвера JDBC включаются как часть собственного настраиваемого пакета установки. Втором подходе используется пакет установки JDBC, предоставляемых корпорацией Майкрософт, который можно загрузить из [драйвера JDBC для SQL Server Developer Center](http://go.microsoft.com/fwlink/?LinkId=70166).  
  
 В следующих разделах описывается использование пакета установки в операционных системах Windows и UNIX.  
  
> [!NOTE]  
>  Дополнительные общие сведения о развертывании приложений Java см. на веб-сайте Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Развертывание драйвера JDBC в системах Windows  
 При развертывании драйвера JDBC в операционных системах Windows, необходимо использовать исполняемый вариант ZIP-файл пакета установки, который обычно называется `sqljdbc_<version>_<language>.exe`.  
  
 Чтобы запустить исполняемый ZIP-файл без вмешательства пользователя, необходимо использовать `/auto` параметр командной строки, в командной строке или в пакетном файле, как описано ниже:  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  При использовании `/auto` параметр не является полностью автоматической установки, как диалоговое окно WinZip по-прежнему отображается на экране пользователя. Однако оно не требует выполнения каких-либо действий пользователя и закрывается после выполнения операции распаковки.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Развертывание драйвера в системах UNIX  
 При развертывании драйвера JDBC в операционных системах UNIX необходимо использовать версию файла gzip пакета установки, который обычно называется `sqljdbc_<version>_<language>.tar.gz`.  
  
 До установки драйвера JDBC необходимо убедиться в том, что в системе пользователя установлены программы gzip и tar, и что папки, содержащие исполняемые файлы обеих программ, добавлены к переменной среды PATH.  
  
 Чтобы распаковать сжатый TAR-файл, перейдите в каталог, в который нужно распаковать драйвер, и введите следующую команду:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Чтобы распаковать TAR-файл, переместите его в каталог, в который нужно установить драйвер, и введите следующую команду:  
  
 `tar –xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
