# My fork of surge (used in my engine)
## A fast bitboard-based legal chess move generator, written in C++
### Features:
* Magic Bitboard sliding attacks and pre-generated attack tables
* Make-Unmake position class
* 16-bit Move representation
* Extremely fast bulk-counted perft (over 180,000,000 NPS, single-threaded, without hashtable)
* Simple design for use in any chess engine

### perft(6) from starting position:
![perft(6)](perft(6).png)

### Getting Started:
```cpp
#include "position.h"
#include "tables.h"
#include "types.h"
#include <iostream>

int main() {
    initialise_all_databases();
    zobrist::initialise_zobrist_keys();
	
    Position p("rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq -");
    std::cout << p;

    MoveList<WHITE> list(p);

    for (Move m : list) {
        std::cout << m << std::endl;
    }
    
    return 0;
}
```
