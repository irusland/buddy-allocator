# Buddy allocation algorithm
## Memory manager

### General settings
1) `maxlevel = 10` constant that represents maximum 2<sup>10</sup> bytes of memory managed by allocator
1) `minlevel = 4` minimum not divisional part in memory

1) Structure Info could contain block information needed for buddy search process

    it will be stored in previous bytes with offset of (-sizeof(Info))
    ```c++
    typedef struct Info {
       uint8_t level;

       Info(uint8_t level) : level(level) {}
    };
    ```
1) Buddy search algorithm: 
    * finding an offset = `address - memory_base`
    * buddy could be found with a bitwise xor `offset ^ blocksize(i)`
    * where `blocksize(i)` is a 2<sup>i</sup> function
    * when returning shift back (add) base memory address
    
> Example:
>
> For offset = 75 on i = 7 level
>
> O = 01001011 (75)
>
> L = 10000000 (2<sup>7</sup>)
>
> B = 11001011 (203)
>
> Buddy address is OxCB for Ox4B block

## Author

* **[Ruslan Sirazhetdinov](https://github.com/irusland)** - *Project creator, UrFU Student*