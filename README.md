# My-first-python-project
# Stanford Code in Place 2021 Final Project: GC-content calculator

# DNA bases : Adenine(A), Thymine(T), Guanine(G) and Cytosine(C)

DEFAULT_SEQ = "SARS-CoV-2.txt"


# get the sequence from the user or set as default

def get_sequence():
    sequence = input("Enter nucleotide sequence (or press enter for default): \n")
    sequence = sequence.upper()
    if sequence == "":
        sequence = DEFAULT_SEQ
    return sequence


# Get the total number of A's , T's, G's and C's present in a given sequence

def accessing_seq(sequence):
    A = 0
    T = 0
    G = 0
    C = 0
    U = 0
    
    if sequence == DEFAULT_SEQ:
        with open(DEFAULT_SEQ) as gene:
            for line in gene:
                line = line.upper()
                for ch in line:
                    if ch == "A":
                        A += 1
                        count_A = A

                    elif ch == "T":
                        T += 1
                        count_T = T

                    elif ch == "G":
                        G += 1
                        count_G = G

                    elif ch == "C":
                        C += 1
                    count_C = C
        return count_A, count_T, count_G, count_C
        #return count_T
        #return count_G
        #return count_C

    else:
        for ch in sequence:
            ch = ch.upper()
            if ch == "A":
                A += 1
                count_A = A 
            
            elif ch == "T":
                T += 1
                count_T = T
            
            elif ch == "G":
                G += 1
                count_G = G
            elif ch == "C":
                C += 1
                count_C = C
        return count_A, count_T, count_G, count_C



# get the total length of a given sequence

def length_of_seq(sequence):
    count = 0
    if sequence == DEFAULT_SEQ:
        with open(DEFAULT_SEQ) as gene:
            line = gene.read()
            for ch in line:
                if ch == "A" or ch == "T" or ch == "G" or ch == "C":
                    count += 1
            length_seq = count
        return length_seq
    else: 
        length_seq = len(sequence)
        return length_seq


def mention_name(sequence):
    if sequence == DEFAULT_SEQ:
        name_it = "Default sequence: SARS-CoV-2"
        return name_it
    return sequence



def main():
    sequence = get_sequence()
    print("")
    name_it = mention_name(sequence)
    print(name_it)

    count_A = accessing_seq(sequence)
    A_count = count_A[0]
    T_count = count_A[1]
    G_count = count_A[2]
    C_count = count_A[3]

    seq_length = length_of_seq(sequence)

    print("The total length of the sequence:",str(seq_length))
    print("The total number of A's:",str(A_count))
    print("The total number of T's:",str(T_count))
    print("The total number of G's:",str(G_count))
    print("The total number of C's:",str(C_count))

    GC = (G_count + C_count)/ seq_length * 100
    GC_content = round(GC,2)

    print("GC content:",str(GC_content) + "%")



if __name__ == '__main__':
    main()
