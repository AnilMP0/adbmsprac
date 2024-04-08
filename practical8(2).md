-- MySQL dump 10.13  Distrib 8.3.0, for Win64 (x86_64)
--
-- Host: localhost    Database: prac2
-- ------------------------------------------------------
-- Server version	8.3.0

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `advising`
--

DROP TABLE IF EXISTS `advising`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `advising` (
  `stno` int NOT NULL,
  `empno` int NOT NULL,
  PRIMARY KEY (`stno`,`empno`),
  KEY `empno` (`empno`),
  CONSTRAINT `advising_ibfk_1` FOREIGN KEY (`stno`) REFERENCES `students` (`stno`),
  CONSTRAINT `advising_ibfk_2` FOREIGN KEY (`empno`) REFERENCES `instructors` (`empno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `advising`
--

LOCK TABLES `advising` WRITE;
/*!40000 ALTER TABLE `advising` DISABLE KEYS */;
INSERT INTO `advising` VALUES (1011,19),(2415,19),(2661,23),(2890,23),(5544,23),(3442,56),(3566,126),(4022,234),(5571,234);
/*!40000 ALTER TABLE `advising` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `courses`
--

DROP TABLE IF EXISTS `courses`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `courses` (
  `cno` varchar(50) NOT NULL,
  `cname` varchar(50) DEFAULT NULL,
  `cr` int DEFAULT NULL,
  `cap` int DEFAULT NULL,
  PRIMARY KEY (`cno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `courses`
--

LOCK TABLES `courses` WRITE;
/*!40000 ALTER TABLE `courses` DISABLE KEYS */;
INSERT INTO `courses` VALUES ('cs110','Introduction to Computing',4,120),('cs210','Computer Programming',4,100),('cs240','Computer Architecture',3,100),('cs310','Data Structures',3,60),('cs350','Higher Level Languages',3,50),('cs410','Software Engineering',3,40),('cs460','Graphics',3,30);
/*!40000 ALTER TABLE `courses` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `grades`
--

DROP TABLE IF EXISTS `grades`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `grades` (
  `stno` int DEFAULT NULL,
  `empno` int DEFAULT NULL,
  `cno` varchar(50) DEFAULT NULL,
  `sem` varchar(10) DEFAULT NULL,
  `year` int DEFAULT NULL,
  `grade` int DEFAULT NULL,
  KEY `stno` (`stno`),
  KEY `empno` (`empno`),
  KEY `cno` (`cno`),
  CONSTRAINT `grades_ibfk_1` FOREIGN KEY (`stno`) REFERENCES `students` (`stno`),
  CONSTRAINT `grades_ibfk_2` FOREIGN KEY (`empno`) REFERENCES `instructors` (`empno`),
  CONSTRAINT `grades_ibfk_3` FOREIGN KEY (`cno`) REFERENCES `courses` (`cno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `grades`
--

LOCK TABLES `grades` WRITE;
/*!40000 ALTER TABLE `grades` DISABLE KEYS */;
INSERT INTO `grades` VALUES (1011,19,'cs110','Fall',2001,40),(2661,19,'cs110','Fall',2001,80),(3566,19,'cs110','Fall',2001,95),(5544,19,'cs110','Fall',2001,100),(1011,23,'cs110','Spring',2002,75),(4022,23,'cs110','Spring',2002,60),(3566,19,'cs240','Spring',2002,100),(5571,19,'cs240','Spring',2002,50),(2415,19,'cs240','Spring',2002,100),(3442,234,'cs410','Spring',2002,60),(5571,234,'cs410','Spring',2002,80),(1011,19,'cs210','Fall',2002,90),(2661,19,'cs210','Fall',2002,70),(3566,19,'cs210','Fall',2002,90),(5571,19,'cs210','Spring',2003,85),(4022,19,'cs210','Spring',2003,70),(5544,56,'cs240','Spring',2003,70),(1011,56,'cs240','Spring',2003,90),(4022,56,'cs240','Spring',2003,80),(2661,234,'cs310','Spring',2003,100),(4022,234,'cs310','Spring',2003,75);
/*!40000 ALTER TABLE `grades` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `instructors`
--

DROP TABLE IF EXISTS `instructors`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `instructors` (
  `empno` int NOT NULL,
  `name` varchar(50) DEFAULT NULL,
  `ranks` varchar(20) DEFAULT NULL,
  `roomno` varchar(10) DEFAULT NULL,
  `telno` varchar(15) DEFAULT NULL,
  PRIMARY KEY (`empno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `instructors`
--

LOCK TABLES `instructors` WRITE;
/*!40000 ALTER TABLE `instructors` DISABLE KEYS */;
INSERT INTO `instructors` VALUES (19,'Evans Robert','Professor','82','7122'),(23,'Exxon George','Professor','90','9101'),(56,'Sawyer Kathy','Assoc Prof','91','5110'),(126,'Davis William','Assoc Prof','72','5411'),(234,'Will Samuel','Assist Prof','90','7024');
/*!40000 ALTER TABLE `instructors` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `students`
--

DROP TABLE IF EXISTS `students`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `students` (
  `stno` int NOT NULL,
  `name` varchar(50) DEFAULT NULL,
  `addr` varchar(255) DEFAULT NULL,
  `city` varchar(50) DEFAULT NULL,
  `state` varchar(2) DEFAULT NULL,
  `zip` varchar(10) DEFAULT NULL,
  PRIMARY KEY (`stno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `students`
--

LOCK TABLES `students` WRITE;
/*!40000 ALTER TABLE `students` DISABLE KEYS */;
INSERT INTO `students` VALUES (1011,'edwards p. david','10 red rd','newton','MA','02159'),(2415,'Grogan A. Mary','8 Walnut St','Malden','MA','02148'),(2661,'Mixon Leatha','100 School St','Brookline','MA','02146'),(2890,'McLane Sandy','30 Case Rd','Boston','MA','02122'),(3442,'Novak Roland','42 Beacon St','Nashua','NH','03060'),(3566,'Pierce Richard','70 Park St','Brookline','MA','02146'),(4022,'Prior Lorraine','8 Beacon St','Boston','MA','02125'),(5544,'Rawlings Jerry','15 Pleasant Dr','Boston','MA','02115'),(5571,'Lewis Jerry','1 Main Rd','Providence','RI','02904');
/*!40000 ALTER TABLE `students` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2024-03-01 23:59:14