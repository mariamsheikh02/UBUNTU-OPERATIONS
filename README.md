# UBUNTU-OPERATIONS
# FIFO Page Replacement Algorithm
pages = list(map(int, input("Enter the page reference string: ").split()))
capacity = int(input("Enter the number of frames: "))

frames = []
page_faults = 0
pointer = 0

print("\nPage\tFrames\t\tStatus")

for i in pages:
    if i not in frames:
        page_faults += 1
        if len(frames) < capacity:
            frames.append(i)
        else:
            frames[pointer] = i
            pointer = (pointer + 1) % capacity
        status = "Page Fault"
    else:
        status = "Hit"
    print(f"{i}\t{frames}\t\t\t{status}")

print("\nTotal Page Faults:", page_faults)
print("Total Page Hits:", len(pages) - page_faults)


# Most Recently Used (MRU) Page Replacement Algorithm
pages = list(map(int, input("Enter the page reference string: ").split()))
capacity = int(input("Enter the number of frames: "))

frames = []
page_faults = 0

print("\nPage\tFrames\t\tStatus")

for i in pages:
    if i not in frames:
        page_faults += 1
        if len(frames) < capacity:
            frames.append(i)
        else:
            frames.pop()
            frames.append(i)
        status = "Page Fault"
    else:
        frames.remove(i)
        frames.append(i)
        status = "Hit"
    print(f"{i}\t{frames}\t\t{status}")

print("\nTotal Page Faults:", page_faults)
print("Total Page Hits:", len(pages) - page_faults)
