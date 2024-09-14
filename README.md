# Exercise_5_CSN

## Done by Fedorov Alexey and Okore Joel

## Exercise:
  Producer-Consumer System with JSON Serialization/Deserialization.
  
## Task: 
  Create a producer-consumer system with two producers and one consumer. The producers will generate data, serialize it to JSON, and place it in a shared queue. The consumer will retrieve items from the queue, deserialize them from JSON, and process
them

## Code Snippets:

  ### Importing necessary libraries, Producer Function:
  The system starts by importing essential libraries: threading, queue, json, random, and time. The queue.Queue creates a thread-safe shared queue for data exchange between producers and consumers. The producer function generates random data, serializes it to JSON, and places it in the queue. To avoid indefinite blocking, it uses a timeout and regularly checks a stop_flag to determine if it should stop. The picture 1 show the source code of the Producer Function
  ![image](https://github.com/user-attachments/assets/f8e6f411-58e8-4205-8297-8985f4339771)
  Picture 1 - Producer Function

  ### Consumer Function:
  The consumer function retrieves items from the queue with a timeout to allow periodic checking of the stop_flag. It deserializes the JSON data and processes it, here by printing it. The function continues to operate until the stop flag is set and the queue is empty. Below is the code snippet of the Consumer Function (pic. 2)
  ![image](https://github.com/user-attachments/assets/a20dd8cc-31f9-48ad-80ac-c308cfef7588)
  Picture 2 - Consumer Function

  ### Main Program:
  The main program starts two producer threads and one consumer thread, all set as daemon threads to ensure they terminate with the main program. It keeps the program running with an infinite loop and catches KeyboardInterrupt to set the stop_flag, signaling threads to stop. After the interrupt, it waits for threads to finish, ensuring a clean shutdown. See picture 3.
  ![image](https://github.com/user-attachments/assets/cc4de1a5-9d7d-4a08-acb2-56da61f18f07)
  Picture 3 - Main Program

  Below is a snapshot of the program executing with 2 producers and 1 consumer. See picture 4. 
  ![image](https://github.com/user-attachments/assets/cc5283bb-ff26-45ae-b13b-c225974483e6)
  Picture 4 - Program run with 2 producers and 1 consumer
  

  Finally, here is a snapshot of the modified code having 3 producers and 2 consumers (pic. 5, 6)
  ![image](https://github.com/user-attachments/assets/bedf32a5-c4a5-4a0d-ba7e-99e0a60b30db)
  Picture 5 - Consumer Function with 3 producers and 2 consumers

  ![image](https://github.com/user-attachments/assets/059b691e-82a6-476b-85f3-962250aed206)
  Picture 6 - Main Program with 3 producers and 2 consumers
  
  
  Below is picture illustrating the program running with 3 producers and 2 consumer (Pic. 7).
  ![image](https://github.com/user-attachments/assets/311af693-8e0c-4607-b08a-4d5ea8d8cd50)
  Picture 7 - Program run with 3 producers and 2 consumers

  When I increased the number of producers to 3 and the number of consumers to 2, the system became more dynamic:
    - Producers: Three threads will be generating and enqueuing data concurrently. This could lead to a higher rate of data production.
    - Consumers: Two threads will be processing data concurrently, potentially increasing the system's overall throughput.

  With more producers, the queue became fuller, but the queue size limit ensures that producers will block if the queue is full. With more consumers, data is processed faster, reducing the time items spend in the queue.
    
  
