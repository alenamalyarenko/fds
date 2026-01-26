Installation guide: 

1) Netcdf-fortran library
   https://github.com/Unidata/netcdf-fortran
   https://docs.unidata.ucar.edu/netcdf-c/current/building_netcdf_fortran.html
      
2) FDS fork
    git clone https://github.com/alenamalyarenko/fds

3) Compilation flags: 
	Source/keys.h

4) Local build on Ubuntu:
  
  Modify makefile, Line 21: NETCDF_LIB=
  Note: in makefile, only one option has been modified to work with netcdf: impi_inter_linux (uc for local compile, nesi for cluster compile)
  Rad on Nesi: https://www.nesi.org.nz/
  
  Run :   Build/compile
  
  
 
 
 New Files:
 Keys.h - compilation keys
 coupled_files.h - module coupled files (holds file names)
 atm_bc_coupled.h - reads netCDF files for bc 
 
 Changed:
 cons.f90 - file managment, coupled_bondary
 dump.f90 - write netcdf files; write init fields at time=0
 init.f90 - acclocate VT_ATM variables; read ic subroutines
 main.f90 - calls to read ic, calls to read bc
 mesh.f90 - extra BC variables, global mesh variables 
 pres.f90 - prescribe normal componment of BC
 read.f90 - new mesh setup; subroutine read_ic
 type.f90 - ATM variables, mesh variables
 velo.f90 - application of bc in velocity_bc; includes atm_bc_coupled and coupled_files
 wall.f90 - Temperature BC ( in  SURFACE_HEAT_TRANSFER)