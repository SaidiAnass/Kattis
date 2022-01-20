import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.BufferedOutputStream;
import java.util.StringTokenizer;
import java.io.IOException;
import java.util.HashMap;

public class teque {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedOutputStream out = new BufferedOutputStream(System.out);

        int n = Integer.parseInt(br.readLine());
        HashMap<Integer, Integer> front = new HashMap<>();
        HashMap<Integer, Integer> back = new HashMap<>();
        int frontHead = -1;
        int frontTail = 0;
        int backHead = -1;
        int backTail = 0;

        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < n; i++) {
            StringTokenizer st = new StringTokenizer(br.readLine());
            String command = st.nextToken();
            int x = Integer.parseInt(st.nextToken());

            if (command.equals("get")) {
                if (x < front.size()) {
                    sb.append(front.get(x + frontHead + 1));
                } else {
                    sb.append(back.get(x - front.size() + backHead + 1));
                }
                sb.append("\n");
                continue;
            }

            if (command.equals("push_back")) {
                back.put(backTail++, x);
            } else if (command.equals("push_front")) {
                front.put(frontHead--, x);
            } else {
                front.put(frontTail++, x);
            }

            if (front.size() < back.size()) {
                front.put(frontTail++, back.get(backHead + 1));
                back.remove(++backHead);
            } else if (front.size() - 1 > back.size()) {
                back.put(backHead--, front.get(frontTail - 1));
                front.remove(--frontTail);
            }

            // if (!front.isEmpty()){
            //     StringBuilder frontStr= new StringBuilder("{");
            //     for (Integer key : front.keySet()) {
            //         frontStr.append(key + "=" + front.get(key) + ", ");
            //     }
            //     frontStr.delete(frontStr.length()-2, frontStr.length()).append("}");
            //     System.out.println(frontStr);
            // }
            //
            // if (!back.isEmpty()) {
            //     StringBuilder backStr= new StringBuilder("{");
            //     for (Integer key : back.keySet()) {
            //         backStr.append(key + "=" + back.get(key) + ", ");
            //     }
            //     backStr.delete(backStr.length()-2, backStr.length()).append("}");
            //     System.out.println(backStr);
            // }
        }

        out.write(sb.toString().getBytes());

        br.close();
        out.close();
    }
}
