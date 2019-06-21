---
title: Развертывание драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b688e5b014915578df5c56ec5e6af2fc8fe26b16
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66781982"
---
# <a name="deploying-the-jdbc-driver"></a>Развертывание драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При развертывании приложения, зависящего от драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], необходимо вместе с приложением распространять драйвер JDBC. В отличие от компонентов доступа к данным Windows DAC, которые являются компонентами операционной системы Windows, драйвер JDBC считается компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для развертывания драйвера JDBC в приложении используются два подхода. При использовании одного файлы драйвера JDBC включаются как часть собственного настраиваемого пакета установки. При втором подходе используется предоставляемый Майкрософт пакет установки JDBC, который можно скачать в [Центре разработки драйвера Microsoft JDBC для SQL Server](https://go.microsoft.com/fwlink/?LinkId=70166).  
  
 В следующих разделах описывается использование пакета установки в операционных системах Windows и UNIX.  
  
> [!NOTE]  
>  Дополнительные общие сведения о развертывании приложений Java см. на веб-сайте Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Развертывание драйвера JDBC в системах Windows  
 При развертывании драйвера JDBC в операционных системах Windows необходимо использовать исполняемый вариант ZIP-файла пакета установки, который обычно называется `sqljdbc_<version>_<language>.exe`.  
  
 Для автоматического запуска исполняемого файла в формате ZIP необходимо использовать параметр командной строки `/auto` в командной строке или пакетном файле, как описано ниже.  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  При использовании параметра `/auto` установка не будет полностью автоматической, так как на экране пользователя все же будет отображаться диалоговое окно WinZip. Однако оно не требует выполнения каких-либо действий пользователя и закрывается после выполнения операции распаковки.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Развертывание драйвера в системах UNIX  
 При развертывании драйвера JDBC в операционных системах UNIX необходимо использовать исполняемый файл в формате GZIP пакета установки, который обычно называется `sqljdbc_<version>_<language>.tar.gz`.  
  
 До установки драйвера JDBC необходимо убедиться в том, что в системе пользователя установлены программы gzip и tar, и что папки, содержащие исполняемые файлы обеих программ, добавлены к переменной среды PATH.  
  
 Чтобы распаковать сжатый TAR-файл, перейдите в каталог, в который нужно распаковать драйвер, и введите следующую команду:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Чтобы распаковать TAR-файл, переместите его в каталог, в который нужно установить драйвер, и введите следующую команду:  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
