############################
#                          #
# Assembly   Converter     #
#                          #
############################


Some of this code is taken from The European Bioinformatics Institute and
Genome Research Limited 
  
Summary
=======

A program to map slices from old assemblies to the latest assembly.


Documentation
=============

For a summary of command line flags, run:

  perl AssemblyMapper.pl --help

Usage:

  AssemblyMapper.pl --species=species --slice=slice

    --species / -s  Name of species.

    --genomes / -g  Automatically sets DB params for e!Genomes

    --slice / -sl    slices needed to map to
                    the most recent assembly.  The format of the data
                    is the same as the output of the name() method on a
                    Slice object:

                      coord_system:version:seq_region_name:start:end:strand

                    For example:

                      chromosome:NCBI36:X:1:10000:1

                    NB:  Mappings are only available for chromosomes to
                    the latest assembly, and only from old assemblies to
                    the latest assembly, not between old assemblies or
                    *from* the latest assembly.

                    If the strand is missing, the positive ("1") strand
                    will be used.

                    If the start is missing, it is taken to be "1".  If
                    the end is missing, it is taken to be the end of the
                    seq_region.

    --help    / -h  To see this text.

Example usage:

  AssemblyMapper.pl -s human -sl chromosome:NCBI34:7:490000:500000:1

An example of the Mapping process

# # chromosome:NCBI34:7:490000:500000:1
#   chromosome:NCBI34:7:490000:491085:1,chromosome:GRCh38:7:705282:706367:1
#   chromosome:NCBI34:7:491086:491158:1,chromosome:GRCh38:7:706369:706441:1
#   chromosome:NCBI34:7:491170:491334:1,chromosome:GRCh38:7:706442:706606:1
#   chromosome:NCBI34:7:491337:493862:1,chromosome:GRCh38:7:706607:709132:1
#  chromosome:NCBI34:7:493863:494116:1,chromosome:GRCh38:7:709136:709389:1
#  chromosome:NCBI34:7:494117:500000:1,chromosome:GRCh38:7:709391:715274:1

