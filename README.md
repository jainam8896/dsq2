# dsq2
import java.util.*;

public class a3q2 {

    static Scanner sc= new Scanner(System.in);

    

    static class node

    {

        int data;

        node left;

        node right;

        node(int data)

        {

            this.data=data;

            this.left=null;

            this.right=null;

        }

    }

    

    static node createtree()

    {

        System.out.println("Enter The Data: ");

        int data = sc.nextInt();

        if(data==-1)

        {

            return null;

        }

        node root = new node(data);

        System.out.println("Enter Data For Left "+data);

        root.left=createtree();

        System.out.println("Enter Data For Right "+data);

        root.right=createtree();

        

        return root;

    }

    

    static void inorder(node root)

    {

        if(root==null)

        {

            return;

        }

        inorder(root.left);

        System.out.println(root.data+" ");

        inorder(root.right);

    }

    

    static void preorder(node root)

    {

        if(root==null)

        {

            return;

        }

        System.out.println(root.data+" ");

        preorder(root.left);

        preorder(root.right);

    }

    

    static void postorder(node root)

    {

        if(root==null)

        {

            return;

        }

        postorder(root.left);

        postorder(root.right);

        System.out.println(root.data+" ");

    }

    

    static node findnode(node root,int key)

    {

        if(root==null) 

        {

            return null;

        }

        if(root.data==key)

        {

            return root;

        }

        node found = findnode(root.left,key);

        if(found!=null)

        {

            return found;

        }

        return findnode(root.right,key);

    }

    

    public static void main(String[] args) {

        node root = createtree();

        System.out.println("In - Order");

        inorder(root);

        System.out.println();

        System.out.println("Pre-Order");

        preorder(root);

        System.out.println();

        System.out.println("PostOrder");

        postorder(root);

        System.out.println();

        

        System.out.println("Enter The Key To Search And Replace In Binary Tree: ");

        int key = sc.nextInt();

        int replaceval = sc.nextInt();

        node foundnode = findnode(root,key);

        if(foundnode==null)

        {

            System.out.println("No data Found");

        }

        else

        {

            node temp = foundnode;

            foundnode.data = replaceval;

            replaceval = temp.data;

            

            System.out.println(foundnode.data+"Is Present In Binary Tree");

            System.out.println("After Replacing");

            System.out.println("In-Order");

            inorder(root);

            System.out.println();

            System.out.println("Pre-Order");

            preorder(root);

            System.out.println();

            System.out.println("Post-Order");

            postorder(root);

            System.out.println();

        }

    }

}
