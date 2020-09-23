---
title: Развертывание JDBC Driver
description: Узнайте, как распространить и развернуть драйвер Microsoft JDBC Driver for SQL Server для приложения и какие файлы для этого необходимы.
ms.custom: ''
ms.date: 07/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 08365944acd071f21b3b4fadf950c23b65c6cfe5
ms.sourcegitcommit: b80364e31739d7b08cc388c1f83bb01de5dd45c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565436"
---
# <a name="deploying-the-jdbc-driver"></a>Развертывание JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

При развертывании приложения, зависящего от драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], необходимо вместе с приложением распространять драйвер JDBC. В отличие от компонентов доступа к данным Windows DAC, которые являются компонентами операционной системы Windows, драйвер JDBC считается компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Для развертывания драйвера JDBC в приложении используются два подхода. При использовании одного файлы драйвера JDBC включаются как часть собственного настраиваемого пакета установки. При втором подходе используется предоставляемый Майкрософт пакет установки JDBC, который можно скачать на [странице загрузки драйвера Microsoft JDBC для SQL Server](download-microsoft-jdbc-driver-for-sql-server.md).  
  
В следующих разделах описывается использование пакета установки в операционных системах Windows и UNIX.  
  
> [!NOTE]  
> Дополнительные общие сведения о развертывании приложений Java см. на веб-сайте Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Развертывание JDBC Driver в системах Windows

При развертывании JDBC Driver в операционных системах Windows необходимо распаковать ZIP-файл пакета установки, который обычно называется `sqljdbc_<version>_<language>.zip`.

## <a name="deploying-the-driver-on-unix-systems"></a>Развертывание JDBC Driver в системах UNIX

При развертывании драйвера JDBC в операционных системах UNIX необходимо использовать исполняемый файл в формате GZIP пакета установки, который обычно называется `sqljdbc_<version>_<language>.tar.gz`.  
  
До установки драйвера JDBC необходимо убедиться в том, что в системе пользователя установлены программы gzip и tar, и что папки, содержащие исполняемые файлы обеих программ, добавлены к переменной среды PATH.  
  
Чтобы распаковать сжатый TAR-файл, перейдите в каталог, в который нужно распаковать драйвер, и введите следующую команду:  
  
`gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
Чтобы распаковать TAR-файл, переместите его в каталог, в который нужно установить драйвер, и введите следующую команду:  
  
`tar -xf sqljdbc_<version>_<language>.tar`  

## <a name="legalities-of-driver-redistribution"></a>Законность распространения драйверов

Драйверы JDBC Driver версий 6.0, 6.2, 6.4, 7.0, 7.2, 7.4, 8.2 и 8.4 являются распространяемыми. В лицензионном соглашении ознакомьтесь с разделом _Распространяемый код_.

Драйверы JDBC версии 4.x являются устаревшими и не поддерживаются. Поддержка версии 4.x прекратилась еще до 2018 г.

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](overview-of-the-jdbc-driver.md)  
