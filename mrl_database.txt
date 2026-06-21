def load_mrl_database(filename):

    mrls = {}

    with open(filename, "r") as file:

        for line in file:

            pesticide, limit = line.strip().split("=")

            mrls[pesticide] = float(limit)

    return mrls


mrls = load_mrl_database("mrl_database.txt")

pesticide = input("Enter pesticide name: ")

value = float(input("Detected residue value: "))

if pesticide in mrls:

    limit = mrls[pesticide]

    print("\nMRL Report")
    print("-" * 20)

    print("Pesticide:", pesticide)
    print("Detected Value:", value)
    print("MRL:", limit)

    if value <= limit:

        print("Status: Within Limit")

    else:

        print("Status: Exceeds MRL")

else:

    print("Pesticide not found in database")