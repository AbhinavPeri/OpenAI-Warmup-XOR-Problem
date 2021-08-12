# OpenAI-Warmup-XOR-Problem
*Solving OpenAI's 1st warmup problem using an LSTM*

Validation Loss
<img width="1185" alt="Screen Shot 2021-08-12 at 6 51 43 PM" src="https://user-images.githubusercontent.com/54607217/129284202-1a087f12-251e-493c-b770-6efb4877cf69.png">

Validation Accuracy
<img width="1184" alt="Screen Shot 2021-08-12 at 6 51 18 PM" src="https://user-images.githubusercontent.com/54607217/129284205-952c3883-0f4c-40e2-a661-6d2219c3d833.png">

Training Loss
<img width="1193" alt="Screen Shot 2021-08-12 at 6 50 43 PM" src="https://user-images.githubusercontent.com/54607217/129284208-144cc9b1-22e2-4bee-97fc-547006fc2ce4.png">

Training Accuracy
<img width="1197" alt="Screen Shot 2021-08-12 at 6 50 22 PM" src="https://user-images.githubusercontent.com/54607217/129284209-97ae0354-4c79-412c-8103-cba7bec658ab.png">
*blue was the variable length model, and orange was the fixed length model*


As you can see, the variable length model has taken longer to converge. This is because the model with fixed size always trains on a sequence of 50 units long while the variable length model trains on sequences that are at most 50 units long. This results in the fixed length model being more exposed to the data, and therefore more penalized to converge to a solution. Initially when I implemented the LSTM solution, I only calculated loss based on the last output of the LSTM. When I tried training it however, it would never converge. Then I realized that by penalizing the model only on the last output, I was allowing it to make mistakes in it's output in the beginning of the sequence. As a result, I could not expect it to perform well on the final output if it did not know how to perform well on the other outputs. This underexposure to the data made it impossible for the model to converge, just like how it is handicapping the variable length model.
