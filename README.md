# fkp-viewer
Fokker-Planck viewer


# файлы 
файл параметров

params.dat - тексторый файл параметров расчета

файлы распределения в полярных координатах:

rho.dat - сетка по R (тексторый формат)  
rho.bin - сетка по R (бинарный формат)

csn.dat - сетка по углу cos(phi) (тексторый формат)  
csn.bin - сетка по углу cos(phi) (бинарный формат)

phi.dat - сетка по углу phi (тексторый формат)  
phi.bin - сетка по углу phi (бинарный формат)

df_{time}.dat - массив распределения  (тексторый формат)  
df_{time}.bin - массив распределения  (тексторый формат)

time - время  
пример имени файла:
df_0.12435.dat


процедура на фортране для записи массива с временем
```fortran
subroutine write_time_array(arr, arr_name, time)
    implicit none
    real(wp), intent(in) :: arr(:)
    character(len=*), intent(in) :: array_name
    real(wp), intent(in) :: time

    integer, parameter :: iu = 20
    character(120) fname

    write(fname,'("results/", A, "_", f9.7,".dat")') arr_name, time
    print *, fname
    open(iu, file=fname)
    write(iu,*) arr
    close(iu)

end subroutine
```

процедура на фортране для записи массива arr с именем arr_name
```fortran
subroutine write_array(arr, arr_name)
    implicit none
    real(wp), intent(in) :: arr(:)
    character(len=*), intent(in) :: array_name

    integer, parameter :: iu = 20
    character(120) fname

    write(fname,'("results/", A, ".dat")') arr_name
    print *, fname
    open(iu, file=fname)
    write(iu,*) arr
    close(iu)

end subroutine
```