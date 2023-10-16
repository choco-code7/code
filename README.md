A set of processes are arranged in a ring.

Each process stores its rank in MPI_COMM_WORLD into an integer variable snd_buf.

Each process passes this on to its neighbor on the right.

Each processor calculates the sum of all values.

Keep passing it around the ring until the value is back where it started, i.e.

each process calculates sum of all ranks.

Use non-blocking MPI_Issend

– to avoid deadlocks

– to verify the correctness, because blocking synchronous send will cause a deadlock
Calculate two separate sums:

–  rank integer sum (as before)

–  rank floating point sum

Use a struct datatype for this

with same fixed memory layout for send and receive buffer.

use int MPI_Type_struct(int count, int \*array_of_blocklengths, MPI_Aint \*array_of_displacements,   MPI_Datatype \*array_of_types, MPI_Datatype \*newtype)
