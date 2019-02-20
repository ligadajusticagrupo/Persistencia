-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema db_conc_jdbc_avaliacao
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema db_conc_jdbc_avaliacao
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `db_conc_jdbc_avaliacao` DEFAULT CHARACTER SET utf8 ;
USE `db_conc_jdbc_avaliacao` ;

-- -----------------------------------------------------
-- Table `db_conc_jdbc_avaliacao`.`tb_alunos`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `db_conc_jdbc_avaliacao`.`tb_alunos` (
  `idtb_alunos` INT NOT NULL AUTO_INCREMENT,
  `aluno` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idtb_alunos`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `db_conc_jdbc_avaliacao`.`tb_cursos`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `db_conc_jdbc_avaliacao`.`tb_cursos` (
  `idcurso` INT NOT NULL,
  `descricao` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idcurso`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `db_conc_jdbc_avaliacao`.`tb_notas`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `db_conc_jdbc_avaliacao`.`tb_notas` (
  `idnota` INT NOT NULL,
  `nota` DOUBLE NULL,
  `tb_alunos_idtb_alunos` INT NOT NULL,
  `tb_cursos_idcurso` INT NOT NULL,
  PRIMARY KEY (`idnota`, `tb_alunos_idtb_alunos`, `tb_cursos_idcurso`),
  INDEX `fk_table1_tb_alunos_idx` (`tb_alunos_idtb_alunos` ASC) VISIBLE,
  INDEX `fk_table1_tb_cursos1_idx` (`tb_cursos_idcurso` ASC) VISIBLE,
  CONSTRAINT `fk_table1_tb_alunos`
    FOREIGN KEY (`tb_alunos_idtb_alunos`)
    REFERENCES `db_conc_jdbc_avaliacao`.`tb_alunos` (`idtb_alunos`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_table1_tb_cursos1`
    FOREIGN KEY (`tb_cursos_idcurso`)
    REFERENCES `db_conc_jdbc_avaliacao`.`tb_cursos` (`idcurso`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
