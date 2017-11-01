# mikes-playground
Dev Ops and other VM configuration Misc Related Items
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/stat.h>
#include <sys/types.h>
#include <errno.h>
#include <sched.h>

int main(int ac, char *av[]) {
    /*********************\
     * set up scheduling *
    \*********************/

    struct sched_param sched;

    sched.sched_priority = 8;        /* set priority */

    if ( sched_setscheduler(getpid(), SCHED_FIFO, &sched) < 0 )
        fprintf(stderr, "SETSCHEDULER failed - err = %s\n", strerror(errno));
    else
        printf("Priority set to \"%d\"\n", sched.sched_priority);

    exit(0);
}
